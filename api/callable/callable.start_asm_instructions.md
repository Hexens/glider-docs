---
description: Returns start assembly instructions of the function/modifier.
---

# Callable.start\_asm\_instructions()

`start_asm_instructions() →` [`Instructions`](../instructions/)

## Query Example

```python
from glider import *

def query():
  functions = Functions().exec(100)

  start_asm_instructions = []
  for function in functions:
    for instruction in function.start_asm_instructions().exec():
      # Return the start assembly instructions for each function
      start_asm_instructions.append(instruction)

  return start_asm_instructions
```

## Output Example

```solidity
[
  {
    "contract": "0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "contract_name": "Address",
    "contract_link": "https://etherscan.io/address/0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "uuid": "5c310d23-5716-4d53-8e23-5bf006ec3713",
    "severity": "",
    "sol_function": 
      function _revert(
        bytes memory returndata, string memory errorMessage
      ) private pure {
        // Look for revert reason and bubble it up if present
        if (returndata.length > 0) {
          // The easiest way to bubble the revert reason is using memory via assembly
          /// @solidity memory-safe-assembly
          assembly {
            let returndata_size := mload(returndata)
            revert(add(32, returndata), returndata_size)
          }
        } else {
          revert(errorMessage);
        }
      }
    "sol_instruction": 
      assembly {
        let returndata_size := mload(returndata)
        revert(add(32, returndata), returndata_size)
      }
  },
  ...
]
```

