# Instructions.external\_calls()

**`external_calls`**`() →` [`Instructions`](./)

Returns the [Instructions](./) object withe all the external call instructions.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of external call instructions
  instructions = Instructions().external_calls().exec(1,100)
  
  return instructions
```

Output:

```json
{
  "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
  "contract_name": "VaultGovernance",
  "sol_function": "function deployVault(
        address[] memory vaultTokens,bytes memory options,address owner
    ) public virtual returns (IVault vault,uint256 nft) {
        require(initialized,Exceptions.INITIALIZATION);
        IProtocolGovernance protocolGovernance = IProtocolGovernance(_internalParams.protocolGovernance);
        require(protocolGovernance.permissionless() || protocolGovernance.isAdmin(msg.sender),Exceptions.PERMISSIONLESS_OR_ADMIN);
        vault = factory.deployVault(vaultTokens,options);
        address nftOwner = owner;
        nft = _internalParams.registry.registerVault(address(vault),nftOwner);
        vault.initialize(nft);
        emit DeployedVault(tx.origin,msg.sender,vaultTokens,options,nftOwner,address(vault),nft);
    }",
  "sol_instruction": "vault = factory.deployVault(vaultTokens,options)"
}
```
