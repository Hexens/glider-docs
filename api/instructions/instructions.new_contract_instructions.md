---
description: Returns an Instructions object for the instructions that create new contract.
---

# Instructions.new\_contract\_instructions()

`new_contract_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().new_contract_instructions().exec(1)

  return instructions  
```

## Output Example

```solidity
[
  {
    "contract": "0xd6d948a7306c93a63c7458898710109611b33e52",
    "contract_name": "VestingFactory",
    "contract_link": "https://etherscan.io/address/0xd6d948a7306c93a63c7458898710109611b33e52",
    "uuid": "9e7beefa-fce6-452f-a30a-fdb5a79577f9",
    "severity": "",
    "sol_function": 
      function createPool(
          uint256 poolShare,
          string memory poolName
      )
          external
          onlyOwner
          checkPercent(poolShare)
          returns (address)
      {
          address poolAddress = address(
              new VestingPool{
                  salt: keccak256(
                      abi.encodePacked(
                          poolShare,
                          address(this),
                          poolName
                      )
                  )
              }(msg.sender)
          );
          poolTotalPercent += poolShare;
          _pools[poolAddress] = PoolInfo(poolShare, 0, poolName);
          emit PoolCreated(poolAddress, poolShare, poolName);
          return poolAddress;
      }
    "sol_instruction": 
      address poolAddress = address(
          new VestingPool{
              salt: keccak256(
                  abi.encodePacked(
                      poolShare,
                      address(this),
                      poolName
                  )
              )
          }(msg.sender)
      );
  }
]
```
