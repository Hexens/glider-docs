---
icon: magnifying-glass
cover: ../.gitbook/assets/Glider QDB.png
coverY: 0
---

# Recommended Vulnerabilities to Query

Some vulnerabilities are more suitable for querying than others. The list below highlights the ones we recommend starting with, though users are welcome to explore and develop their own ideas for queries.

Difficulty is based on how hard it would be to write a query that will have near 100% true positive hits while being completely new to Glider.

### Easy

* Access Control issues
* Missing onlyOwner on critical functions
* Tx.origin == msg.sender checks which became bypassable after the latest Ethereum Update
* Any bugs that are dependent on old vulnerable versions of contracts, like old versions of OZ contracts
* Public self destructs without authentication
* Transfer calls with OZ IERC20

### Medium

* Swap calls to various Defi apps with slippage hardcoded to 0
* Non EIP-712 compliant signature usage
* Basic re-entrancy issues
* Delegate call to user inputted address without checks
* Arbitrary call without any authentication or checks
* Spot price usage in oracles
* Forked projects with the same bug as its original code

### Hard

<details>

<summary>Native asset double spending on some chains</summary>



1. On certain EVM-based chains, the native asset may have an ERC20-like interface and a designated contract address. For example, in the CELO chain, the native asset can be transferred either through msg.value or through the ERC20-like methods of the GoldToken[ contract](https://explorer.celo.org/mainnet/address/0x471EcE3750Da237f93B8E339c536989b8978a438/contracts#address-tabs), as documented here:[ https://docs.celo.org/developer/migrate/from-ethereum#the-celo-native-asset-and-the-celo-dollar.](https://docs.celo.org/developer/migrate/from-ethereum#the-celo-native-asset-and-the-celo-dollar.) This dual transfer method can create ambiguity and lead to double spending of native asset, if PancakeSwap protocol is deployed on such chains.

An attack exploiting this vulnerability could unfold as follows:

1. The attacker possesses an amount X of native assets, transferable either through msg.value or the ERC20-like contract at address Addr.
2. The attacker initiates Vault.sync() for Addr. There is no need to call sync() for the second time when the native asset is transferred through msg.value, or currency = address(0).
3. The attacker performs two settle operations: Vault.settle(0) with msg.value, and subsequent Vault.settle(Addr).
4. By executing two take operations, the attacker can retrieve back 2X amount of native asset: Vault.take(Addr) and Vault. take(0).

```
function sync(Currency currency) public returns (uint256 balance) {
    balance = currency.balanceOfSelf();
    currency.setVaultReserves(balance);
}

/// @inheritdoc IVault
function settle(Currency currency) external payable override isLocked returns (uint256 paid) {
    if (!currency.isNative()) {
        if (msg.value > 0) revert SettleNonNativeCurrencyWithValue();
        uint256 reservesBefore = currency.getVaultReserves();
        uint256 reservesNow = sync(currency);
        paid = reservesNow - reservesBefore;
    } else {
        paid = msg.value;
    }

    SettlementGuard.accountDelta(msg.sender, currency, paid.toInt128());
}
```

</details>

<details>

<summary>The Eigenlayer merkle proof issue</summary>

In order for the EigenPod to verify and consequently process a withdrawal from the beacon chain, it uses the BeaconChainsProofs' verifyWithdrawal function. This function takes various parameters to prove the existence of a supplied Withdrawal struct in the beacon chain state Merkle root.

To do so, it proves 5 different leaves: the block root against the beacon state root, the slot number against the block root, the execution root against the block root, the timestamp against the execution root and finally the withdrawal against the execution root.

The first proof is not fully checked and it is vulnerable to tampering. Because the other proofs all depend on this first proof, it also influences the others and allows for tampering there as well.

The block root is proven against the beacon state root by first traversing to the historical summaries root in the beacon state. This is done using a constant HISTORICAL\_SUMMARIES\_INDEX which is then concatenated with the historicalSummaryIndex that is supplied by the user to choose the right historical summary root from the Merkle tree. This is again concatenated with blockRootIndex, also supplied by the user to choose the right block from the historical summary tree.

To make sure that the user does not control the flow of traversal through the Merkle tree, it is important to make sure that the proof lengths are of correct lengths and that the bit size of indexes are not greater than the tree height. This is done correctly for each proof, except for the historySummaryIndex, which is missing a size check.

For example, blockRootIndex is check on lines 279-282:

```
require(
    withdrawalProof.blockRootIndex < 2 ** BLOCK_ROOTS_TREE_HEIGHT,
    "BeaconChainProofs.verifyWithdrawal: blockRootIndex is too large"
);
```

But historySummaryIndex is missing such checks.

This allows a malicious user to provide an index greater than the tree height. If this were a simple, single Merkle tree with one index, then it would not be problem. But in this case we are traversing combinations of multiple trees from the beacon state root to the block root and so it allows for other indexes to be overwritten.

For example, in the first proof the combined index for the proof is calculated using the concatenations as described above:

```
uint256 historicalBlockHeaderIndex = (HISTORICAL_SUMMARIES_INDEX <<
    ((HISTORICAL_SUMMARIES_TREE_HEIGHT + 1) + 1 + (BLOCK_ROOTS_TREE_HEIGHT))) |
    (uint256(withdrawalProof.historicalSummaryIndex) << (1 + (BLOCK_ROOTS_TREE_HEIGHT))) |
    (BLOCK_SUMMARY_ROOT_INDEX << (BLOCK_ROOTS_TREE_HEIGHT)) |
    uint256(withdrawalProof.blockRootIndex);
```

As can be seen, the historySummaryIndex is appended on top of the constant HISTORICAL\_SUMMARIES\_INDEX (which should ensure that we first traverse from the beacon state root to the history summaries root). Now that historySummaryIndex is unbounded, it becomes possible to overwrite the HISTORY\_SUMMARIES\_INDEX to any value and make the traversal go into any other field of the beacon state instead:[ https://github.com/ethereum/consensus-specs/blob/dev/specs/capella/beacon-chain.md#beaconstate](https://github.com/ethereum/consensus-specs/blob/dev/specs/capella/beacon-chain.md#beaconstate)

In order to exploit this bug and forge a withdrawal proof, it becomes important to plan a path where the proofs will go and result in valid values for the withdrawal struct.

For example, the first proof provides a lot of freedom in traversing from the historicalSummaryIndex and blockRootIndex.

The timestamp, slot and execution root proofs can be ignored as the proof lengths are short and they can simply pass with a hash value as leaf. The hash value would be interpreted as timestamp and slot, which will not make any checks fails, rather it gives unique timestamps and slots which could give either full or partial withdrawals depending on the validator’s withdrawable epoch.

Only the withdrawal proof will require some planning, as the withdrawal fields will either have to be some other leaf value or brute-forced hashes (intermediate leaves) in some part of the entire beacon state Merkle tree. Brute-forced hashes would still work, as the only used fields from the withdrawal struct are the validator index (which is parsed into 5 bytes) and the withdrawal amount (which is parsed into 8 bytes, expressed in Gwei and should be not too large).

A working exploit would allow a malicious user to proof withdrawals for themselves or victim users. If the timestamp could be controlled, then it can also be used to proof 0 amount withdrawals for victim users that have a real withdrawal at some timestamp. The timestamp would be set to true and they cannot prove the actual withdrawal anymore, locking their ETH.\


```
function verifyWithdrawal(
        bytes32 beaconStateRoot,
        bytes32[] calldata withdrawalFields,
        WithdrawalProof calldata withdrawalProof
    ) internal view {
        require(
            withdrawalFields.length == 2 ** WITHDRAWAL_FIELD_TREE_HEIGHT,
            "BeaconChainProofs.verifyWithdrawal: withdrawalFields has incorrect length"
        );

        require(
            withdrawalProof.blockRootIndex < 2 ** BLOCK_ROOTS_TREE_HEIGHT,
            "BeaconChainProofs.verifyWithdrawal: blockRootIndex is too large"
        );
        require(
            withdrawalProof.withdrawalIndex < 2 ** WITHDRAWALS_TREE_HEIGHT,
            "BeaconChainProofs.verifyWithdrawal: withdrawalIndex is too large"
        );

        require(
            withdrawalProof.withdrawalProof.length ==
                32 * (EXECUTION_PAYLOAD_HEADER_FIELD_TREE_HEIGHT + WITHDRAWALS_TREE_HEIGHT + 1),
            "BeaconChainProofs.verifyWithdrawal: withdrawalProof has incorrect length"
        );
        require(
            withdrawalProof.executionPayloadProof.length ==
                32 * (BEACON_BLOCK_HEADER_FIELD_TREE_HEIGHT + BEACON_BLOCK_BODY_FIELD_TREE_HEIGHT),
            "BeaconChainProofs.verifyWithdrawal: executionPayloadProof has incorrect length"
        );
        require(
            withdrawalProof.slotProof.length == 32 * (BEACON_BLOCK_HEADER_FIELD_TREE_HEIGHT),
            "BeaconChainProofs.verifyWithdrawal: slotProof has incorrect length"
        );
        require(
            withdrawalProof.timestampProof.length == 32 * (EXECUTION_PAYLOAD_HEADER_FIELD_TREE_HEIGHT),
            "BeaconChainProofs.verifyWithdrawal: timestampProof has incorrect length"
        );

        require(
            withdrawalProof.historicalSummaryBlockRootProof.length ==
                32 *
                    (BEACON_STATE_FIELD_TREE_HEIGHT +
                        (HISTORICAL_SUMMARIES_TREE_HEIGHT + 1) +
                        1 +
                        (BLOCK_ROOTS_TREE_HEIGHT)),
            "BeaconChainProofs.verifyWithdrawal: historicalSummaryBlockRootProof has incorrect length"
        );
        /**
         * Note: Here, the "1" in "1 + (BLOCK_ROOTS_TREE_HEIGHT)" signifies that extra step of choosing the "block_root_summary" within the individual
         * "historical_summary". Everywhere else it signifies merkelize_with_mixin, where the length of an array is hashed with the root of the array,
         * but not here.
         */
        uint256 historicalBlockHeaderIndex = (HISTORICAL_SUMMARIES_INDEX <<
            ((HISTORICAL_SUMMARIES_TREE_HEIGHT + 1) + 1 + (BLOCK_ROOTS_TREE_HEIGHT))) |
            (uint256(withdrawalProof.historicalSummaryIndex) << (1 + (BLOCK_ROOTS_TREE_HEIGHT))) |
            (BLOCK_SUMMARY_ROOT_INDEX << (BLOCK_ROOTS_TREE_HEIGHT)) |
            uint256(withdrawalProof.blockRootIndex);

        require(
            Merkle.verifyInclusionSha256({
                proof: withdrawalProof.historicalSummaryBlockRootProof,
                root: beaconStateRoot,
                leaf: withdrawalProof.blockRoot,
                index: historicalBlockHeaderIndex
            }),
            "BeaconChainProofs.verifyWithdrawal: Invalid historicalsummary merkle proof"
        );

        //Next we verify the slot against the blockRoot
        require(
            Merkle.verifyInclusionSha256({
                proof: withdrawalProof.slotProof,
                root: withdrawalProof.blockRoot,
                leaf: withdrawalProof.slotRoot,
                index: SLOT_INDEX
            }),
            "BeaconChainProofs.verifyWithdrawal: Invalid slot merkle proof"
        );

        {
            // Next we verify the executionPayloadRoot against the blockRoot
            uint256 executionPayloadIndex = (BODY_ROOT_INDEX << (BEACON_BLOCK_BODY_FIELD_TREE_HEIGHT)) |
                EXECUTION_PAYLOAD_INDEX;
            require(
                Merkle.verifyInclusionSha256({
                    proof: withdrawalProof.executionPayloadProof,
                    root: withdrawalProof.blockRoot,
                    leaf: withdrawalProof.executionPayloadRoot,
                    index: executionPayloadIndex
                }),
                "BeaconChainProofs.verifyWithdrawal: Invalid executionPayload merkle proof"
            );
        }

        // Next we verify the timestampRoot against the executionPayload root
        require(
            Merkle.verifyInclusionSha256({
                proof: withdrawalProof.timestampProof,
                root: withdrawalProof.executionPayloadRoot,
                leaf: withdrawalProof.timestampRoot,
                index: TIMESTAMP_INDEX
            }),
            "BeaconChainProofs.verifyWithdrawal: Invalid blockNumber merkle proof"
        );

        {
            /**
             * Next we verify the withdrawal fields against the blockRoot:
             * First we compute the withdrawal_index relative to the blockRoot by concatenating the indexes of all the
             * intermediate root indexes from the bottom of the sub trees (the withdrawal container) to the top, the blockRoot.
             * Then we calculate merkleize the withdrawalFields container to calculate the the withdrawalRoot.
             * Finally we verify the withdrawalRoot against the executionPayloadRoot.
             *
             *
             * Note: Merkleization of the withdrawals root tree uses MerkleizeWithMixin, i.e., the length of the array is hashed with the root of
             * the array.  Thus we shift the WITHDRAWALS_INDEX over by WITHDRAWALS_TREE_HEIGHT + 1 and not just WITHDRAWALS_TREE_HEIGHT.
             */
            uint256 withdrawalIndex = (WITHDRAWALS_INDEX << (WITHDRAWALS_TREE_HEIGHT + 1)) |
                uint256(withdrawalProof.withdrawalIndex);
            bytes32 withdrawalRoot = Merkle.merkleizeSha256(withdrawalFields);
            require(
                Merkle.verifyInclusionSha256({
                    proof: withdrawalProof.withdrawalProof,
                    root: withdrawalProof.executionPayloadRoot,
                    leaf: withdrawalRoot,
                    index: withdrawalIndex
                }),
                "BeaconChainProofs.verifyWithdrawal: Invalid withdrawal merkle proof"
            );
        }
    }
```

</details>

<details>

<summary>Draining ETH using flat fee without msg.value chec</summary>

In the contracts/DvBridge.sol when the user calls the initiateTransfer() at the end of it the function calls the rewardValidators() function which distributes rewards to the validators. However the way it’s implemented currently allows a malicious user to slowly drain the pool or even steal native funds from the bridge because when initiating a transfer the function doesn’t check wether the user has supplied enough native funds to distribute rewards to the validators and because the fee that’s being distributed to the validators is a flat fee not a percentage of the msg.value it allows the user to initiate a transfer supplying 1 wei of native funds but distributing much more native funds to the validators and in some cases even gaining profit because the remainder of the fee is being sent back to the msg.sender as can be seen here:

contracts/DvBridge.sol:L32-55

```
function initiateTransfer(address recipient, uint256 amount, uint256 source_chain, uint256 destination_chain, address token_in, address token_out) public payable returns (bool) {
        // Validation checks
        require(recipient != address(0), "Recipient cannot be zero address");
        require(amount > 0, "Amount cannot be zero");
        require(source_chain == chain_id, "Invalid source chain");
        require(destination_chain != chain_id, "Invalid destination chain");
        require(isTransferAllowed(destination_chain, token_in, token_out, amount), "Transfer not allowed or amount exceeds maximum allowed");
        
        if(lock_time > block.timestamp) {
            revert("Bridge is locked for transfers");
        }

        // Transfer tokens to the contract
        __allowance(_msgSender(), amount, token_in);
        __transfer(address(this), amount, token_in, true);

        // Emit event for transfer initiation
        emit TransferInitiated(_msgSender(), recipient, amount, source_chain, destination_chain, token_in, token_out);
        
        // Reward validators
        rewardValidators(validator_fee);

        return true;
    }
```

contracts/ValidatorSignatureManager.sol:L54-63

```
 function rewardValidators(uint256 validator_fee) internal {
        uint256 amount = validator_fee / validators.length;
        uint256 remainder = validator_fee % validators.length;

        for (uint256 i = 0; i < validators.length; i++) {
            payable(validators[i]).transfer(amount);
        }

        payable(msg.sender).transfer(remainder);
    }
```

</details>

<details>

<summary>Using duplicate signatures to bypass quotas</summary>

In the contracts/DvBridge.sol the validators can sign messages to authorize the removal or approval of new validators, authorize transactions or change the validator reward fee. However for some action to take place >50% of validators need to sign a message authorizing the action as can be seen in the contracts/ValidatorSignatureManager.sol contract:

contracts/ValidatorSignatureManager.sol:L39-51

```
function verifySignatures(bytes32 message, bytes[] memory signatures) internal view returns (bool) {
        uint256 count = 0;
        for (uint256 i = 0; i < signatures.length; i++) {
            address signer = message.recover(signatures[i]);
            if (isValidator(signer)) {
                count++;
                if (count > validators.length / 2) {
                    return true;
                }
            }
        }
        return false;
    }
```

However because the function doesn’t check wether the given signatures in the array are different or no, any action can be completed by filling the signatures array with the same signature over and over again until the count variable goes over the validators.length / 2 threshold.

(5) PATH: foundry\_contracts/HibachiEscape.sol\
risc\_zero\_verification/asset\_value\_guest/src/bin/hibachi\_asset\_value.rs\
The methods redeemNetEquityForTokens and redeemTokensForNetEquity utilize ZK proofs from Risc0 to redeem net equity for a specified address when the protocol is frozen. An arbitrary user can replay the proof from other transactions for their address to mint redemption tokens for themselves, and similarly for burning tokens.

```
function redeemNetEquityForTokens(uint256[] calldata output, bytes calldata seal, address accountAddress)
    external
    override
    frozen
    accountOwner(accountAddress)
    mainChain
{
    bytes memory journal = abi.encode(output);

    verifier.verify(seal, assetValueProgramImageId, sha256(journal));

    if (output.length != 4) {
        revert StateUpdateInvalid();
    }

    uint256 assetId = output[1];
    uint256 quantity = output[2];
    uint256 netEquityValue = output[3];

    if (netEquity[accountAddress] < netEquityValue) {
        revert AmountTooHigh();
    }

    netEquity[accountAddress] -= netEquityValue;

    _mintRedemptionTokens(assetId, _msgSender(), quantity);
}
```

```
function redeemTokensForNetEquity(uint256[] calldata output, bytes calldata seal, address accountAddress)
    external
    override
    frozen
    accountOwner(accountAddress)
    mainChain
{
    bytes memory journal = abi.encode(output);

    verifier.verify(seal, assetValueProgramImageId, sha256(journal));

    if (output.length != 4) {
        revert StateUpdateInvalid();
    }

    uint256 assetId = output[1];
    uint256 quantity = output[2];
    uint256 netEquityValue = output[3];

    netEquity[accountAddress] += netEquityValue;

    _burnRedemptionTokens(assetId, _msgSender(), quantity);
}
```

The problem arises as the journal doesn’t contains replay protection:

```
let calldata_vec = vec![
    DynSolValue::Uint(collateral_asset_id, 256),
    DynSolValue::Uint(asset_id, 256),
    DynSolValue::Uint(quantity, 256),
    DynSolValue::Uint(value, 256),
];

let ret_array = DynSolValue::Array(calldata_vec);

// Commit the journal that will be received by the application contract.
// Encoded types should match the args expected by the application callback.
env::commit_slice(ret_array.abi_encode().as_slice());

```

</details>

<details>

<summary>Exploitable first depositor attacks on ERC-4626 without any protections in place</summary>

No additional description

</details>

<details>

<summary>Decimal precision issues</summary>

No additional description

</details>
