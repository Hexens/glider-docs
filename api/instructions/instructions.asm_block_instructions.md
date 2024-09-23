---
description: >-
  Returns an Instructions object for the instructions that are from assembly
  block.
---

# Instructions.asm\_block\_instructions()

`asm_block_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().asm_block_instructions().exec(2)

  return instructions  
```

## Output Example

```solidity
[
  {
    "contract": "0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e",
    "contract_name": "BAYCOthersideLand",
    "contract_link": "https://etherscan.io/address/0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e",
    "uuid": "cde0ad30-0c1a-4dc2-aa9e-b70b3b1b6764",
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
    "sol_instruction": "calldatacopy(0, 0, calldatasize())"
  },
  {
    "contract": "0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e",
    "contract_name": "BAYCOthersideLand",
    "contract_link": "https://etherscan.io/address/0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e",
    "uuid": "c6bcbcc2-ca97-44e6-8607-4938a0bc23b4",
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
    "sol_instruction": "result"
  }
]
```
