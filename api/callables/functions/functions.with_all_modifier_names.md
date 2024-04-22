# Functions.with\_all\_modifier\_names()

`with_all_modifier_names(names: List[str], sensitivity: bool = True) →` [`Functions`](./)

Adds a filter to get functions that have modifiers with all the given names.

## Example

```python
from glider import *

def query():
  functions = Functions().with_all_modifier_names(['lock', 'onlyOwner']).exec(1)

  return functions
```

## Output

```solidity
"root":{3 items
"contract":string"0xde2d96e1dd54ee638c7570601eaa4bd264beee21"
"contract_name":string"MonoMigrator"
"sol_function":solidity
function refund(address accountAddress, address tokenAddress)
        external
        lock
        onlyOwner
    {
        // Fetch amount of tokens to return
        uint256 amountToReturn = tokensMigratedByAccount[tokenAddress][
            accountAddress
        ];
        tokensMigratedByAccount[tokenAddress][accountAddress] = 0; // Set user token balance to zero
        tokensMigratedByToken[tokenAddress] -= amountToReturn; // Decrement global token amount migrated for this token
        IERC20(tokenAddress).transfer(accountAddress, amountToReturn); // Return tokens to user
    }
}
```
