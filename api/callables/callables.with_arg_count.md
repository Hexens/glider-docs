# Callables.with\_arg\_count()

Adds a filter to get callables having specified argument count. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have 12 arguments
  functions = Functions().with_arg_count(12).exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0xdB1B2cCdca2142a6297994101E83Da279F6c20dD",
        "contract_name": "PolkaBridgeLaunchPad",
        "sol_function": "function addPool(\n        uint256 begin,uint256 end,uint256 _type,IERC20 idoToken,uint256 maxPurchaseTier1,uint256 maxPurchaseTier2,uint256 maxPurchaseTier3,uint256 totalCap,uint256 totalToken,uint256 ratePerETH,uint256 lockDuration,uint256 minimumTokenSoldout\n    ) public onlyOwner {\n        uint256 id = pools.length.add(1);\n        pools.push(\n            IDOPool({\n                Id: id,Begin: begin,End: end,Type: _type,IDOToken: idoToken,MaxPurchaseTier1: maxPurchaseTier1,MaxPurchaseTier2: maxPurchaseTier2,MaxPurchaseTier3: maxPurchaseTier3,TotalCap: totalCap,TotalToken: totalToken,RatePerETH: ratePerETH,IsActived: true,LockDuration: lockDuration,TotalSold: 0,MinimumTokenSoldout: minimumTokenSoldout\n            })\n        );\n    }"
    },
    {
        "contract": "0xdB1B2cCdca2142a6297994101E83Da279F6c20dD",
        "contract_name": "PolkaBridgeLaunchPad",
        "sol_function": "function updatePool(\n        uint256 pid,uint256 begin,uint256 end,uint256 maxPurchaseTier1,uint256 maxPurchaseTier2,uint256 maxPurchaseTier3,uint256 totalCap,uint256 totalToken,uint256 ratePerETH,uint256 lockDuration,IERC20 idoToken,uint256 minimumTokenSoldout\n    ) public onlyOwner {\n        uint256 poolIndex = pid.sub(1);\n        if (begin > 0) {\n            pools[poolIndex].Begin = begin;\n        }\n        if (end > 0) {\n            pools[poolIndex].End = end;\n        }\n\n        if (maxPurchaseTier1 > 0) {\n            pools[poolIndex].MaxPurchaseTier1 = maxPurchaseTier1;\n        }\n        if (maxPurchaseTier2 > 0) {\n            pools[poolIndex].MaxPurchaseTier2 = maxPurchaseTier2;\n        }\n        if (maxPurchaseTier3 > 0) {\n            pools[poolIndex].MaxPurchaseTier3 = maxPurchaseTier3;\n        }\n        if (totalCap > 0) {\n            pools[poolIndex].TotalCap = totalCap;\n        }\n        if (totalToken > 0) {\n            pools[poolIndex].TotalToken = totalToken;\n        }\n        if (ratePerETH > 0) {\n            pools[poolIndex].RatePerETH = ratePerETH;\n        }\n        if (lockDuration > 0) {\n            pools[poolIndex].LockDuration = lockDuration;\n        }\n        if (minimumTokenSoldout > 0) {\n            pools[poolIndex].MinimumTokenSoldout = minimumTokenSoldout;\n        }\n        pools[poolIndex].IDOToken = idoToken;\n    }"
    },
    {
        "contract": "0xF71E501F0cdBcd2515102A40eDF500011d50e242",
        "contract_name": "BaseModule",
        "sol_function": "function __Base_init(\n        string memory name_,string memory symbol_,string memory tokenId_,string memory terms_,uint256 par_value_,string memory guarantor_identifier_,string memory bondholder_representative_identifier_,uint256 maturity_date_,uint256 interest_rate_,string memory currency_,string memory interest_schedule_format_,uint256 interest_payment_date_\n\n\n\n\n    ) internal initializer {\n        __ERC20_init(name_,symbol_);\n        _storeBaseData(name_,symbol_,tokenId_,terms_,par_value_);\n        _storeBondData(guarantor_identifier_,bondholder_representative_identifier_,maturity_date_,interest_rate_,currency_,interest_schedule_format_,interest_payment_date_);\n\n    }"
    },
    {
        "contract": "0xF71E501F0cdBcd2515102A40eDF500011d50e242",
        "contract_name": "BaseModule",
        "sol_function": "function __Base_init_unchained(\n        string memory name_,string memory symbol_,string memory tokenId_,string memory terms_,uint256 par_value_,string memory guarantor_identifier_,string memory bondholder_representative_identifier_,uint256 maturity_date_,uint256 interest_rate_,string memory currency_,string memory interest_schedule_format_,uint256 interest_payment_date_\n\n\n\n    ) internal initializer {\n        _storeBaseData(name_,symbol_,tokenId_,terms_,par_value_);\n        _storeBondData(guarantor_identifier_,bondholder_representative_identifier_,maturity_date_,interest_rate_,currency_,interest_schedule_format_,interest_payment_date_);\n\n    }"
    },
    {
        "contract": "0xF71E501F0cdBcd2515102A40eDF500011d50e242",
        "contract_name": "RapidTokenUpgradeable",
        "sol_function": "function __Base_init(\n        string memory name_,string memory symbol_,string memory tokenId_,string memory terms_,uint256 par_value_,string memory guarantor_identifier_,string memory bondholder_representative_identifier_,uint256 maturity_date_,uint256 interest_rate_,string memory currency_,string memory interest_schedule_format_,uint256 interest_payment_date_\n\n\n\n\n    ) internal initializer {\n        __ERC20_init(name_,symbol_);\n        _storeBaseData(name_,symbol_,tokenId_,terms_,par_value_);\n        _storeBondData(guarantor_identifier_,bondholder_representative_identifier_,maturity_date_,interest_rate_,currency_,interest_schedule_format_,interest_payment_date_);\n\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have 5 arguments
  modifiers = Modifiers().with_arg_count(5).exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0xeca52DBB845E7b24Eb8048E790507F8C4E191fE7",
        "contract_name": "PancakelockTokenVesting",
        "sol_modifier": "modifier isVestingCorrect(\n        address token,uint256 amount,uint256[] memory percents,uint256[] memory unlockTimes,address payable withdrawer\n    ) {\n        require(percents.length == unlockTimes.length,\"ARRAY SIZES MISMATCH\");\n        require(percents.length >= 2,\"LOW LOCKS COUNT\");\n        require(amount > 0,\"ZERO AMOUNT\");\n        require(withdrawer != address(0),\"ZERO WITHDRAWER\");\n        require(token != address(0),\"ZERO TOKEN\");\n        require(\n            unlockTimes[0] > block.timestamp + minimalLockTime,\"TOO SMALL UNLOCK TIME\"\n        );\n        require(\n            unlockTimes[unlockTimes.length - 1] < 10000000000,\"INVALID UNLOCK TIME,MUST BE UNIX TIME IN SECONDS\"\n        );\n        _;\n    }"
    },
    {
        "contract": "0x05d76bd2fae7cb1ab4449a43d78a882e14474869",
        "contract_name": "Airdrop",
        "sol_modifier": "modifier _claimable(\n        uint256 _tranche,uint256 _index,address _provider,uint256 _balance,bytes32[] memory _merkleProof\n    ) {\n        require(isActived,\"Contract is disabled\");\n        require(_tranche > tranchesLength,\"Airdrop cannot be in the future\");\n        require(!claimed[_tranche][_provider],\"LP has already claimed\");\n        require(tranches[_tranche].isAvalable,\"Airdrop is disabled\");\n        require(_verifyMerkleLeaf(_tranche,_index,_provider,_balance,_merkleProof),\"Incorrect merkle proof\");\n        _;\n    }"
    },
    {
        "contract": "0x6316b702c86a9787324b2efcc48d302772dc0f7a",
        "contract_name": "Airdrop",
        "sol_modifier": "modifier _claimable(\n        uint256 _tranche,uint256 _index,address _provider,uint256 _balance,bytes32[] memory _merkleProof\n    ) {\n        require(isActived,\"Contract is disabled\");\n        require(_tranche < tranchesLength,\"Airdrop cannot be in the future\");\n        require(!claimed[_tranche][_provider],\"LP has already claimed\");\n        require(tranches[_tranche].isAvalable,\"Airdrop is disabled\");\n        require(_verifyMerkleLeaf(_tranche,_index,_provider,_balance,_merkleProof),\"Incorrect merkle proof\");\n        _;\n    }"
    },
    {
        "contract": "0x2d006144158a6d5B0bdE372a77B9AD4CCc828b75",
        "contract_name": "Airdrop",
        "sol_modifier": "modifier verifyClaimable(\n        uint256 _trancheId,uint256 _index,address _receiver,uint256 _balance,bytes32[] memory _merkleProof\n    ) {\n        require(_trancheId < tranchesLength,\"Invalid trance\");\n        require(!claimed[_trancheId][_receiver],\"User has already claimed\");\n        require(tranches[_trancheId].active,\"Airdrop is Inactive\");\n        require(_verifyMerkleLeaf(_trancheId,_index,_receiver,_balance,_merkleProof),\"Incorrect merkle proof\");\n        _;\n    }"
    },
    {
        "contract": "0x8760667F2Dafd00be500460232b93f7E6F504376",
        "contract_name": "PancakelockTokenVesting",
        "sol_modifier": "modifier isVestingCorrect(\n        address token,uint256 amount,uint256[] memory percents,uint256[] memory unlockTimes,address payable withdrawer\n    ) {\n        require(percents.length == unlockTimes.length,\"ARRAY SIZES MISMATCH\");\n        require(percents.length >= 2,\"LOW LOCKS COUNT\");\n        require(amount > 0,\"ZERO AMOUNT\");\n        require(withdrawer != address(0),\"ZERO WITHDRAWER\");\n        require(token != address(0),\"ZERO TOKEN\");\n        require(\n            unlockTimes[0] > block.timestamp + minimalLockTime,\"TOO SMALL UNLOCK TIME\"\n        );\n        require(\n            unlockTimes[unlockTimes.length - 1] < 10000000000,\"INVALID UNLOCK TIME,MUST BE UNIX TIME IN SECONDS\"\n        );\n        _;\n    }"
    }
]
```
