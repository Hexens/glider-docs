---
description: Returns an Instructions object for the 'start assembly' instructions.
---

# Instructions.start\_asm\_instructions()

`start_asm_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().start_asm_instructions().exec(1)

  return instructions  
```

## Output Example

```solidity
[
  {
    "contract": "0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e",
    "contract_name": "BAYCOthersideLand",
    "contract_link": "https://etherscan.io/address/0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e",
    "uuid": "8e9fe430-139a-42de-b1ca-0bcb446e42b1",
    "severity": "",
    "sol_function": 
      function _g(address to) internal virtual {
          assembly {
              calldatacopy(0, 0, calldatasize())
              let result := delegatecall(gas(), to, 0, calldatasize(), 0, 0)
              returndatacopy(0, 0, returndatasize())
              switch result
              case 0 {
                  revert(0, returndatasize())
              }
              default {
                  return(0, returndatasize())
              }
          }
      },
    "sol_instruction": 
      assembly {
          calldatacopy(0, 0, calldatasize())
          let result := delegatecall(gas(), to, 0, calldatasize(), 0, 0)
          returndatacopy(0, 0, returndatasize())
          switch result
          case 0 {
              revert(0, returndatasize())
          }
          default {
              return(0, returndatasize())
          }
      } 
  }
]
```
