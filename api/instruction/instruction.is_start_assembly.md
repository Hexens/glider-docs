---
description: >-
  Returns true if the instruction is start assembly instruction, otherwise
  returns false.
---

# Instruction.is\_start\_assembly()

`is_start_assembly() -> bool`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(50, 200)
        .filter(lambda inst : inst.is_start_assembly())
    )
            
    return instructions
```

## Output Example

```solidity
[
  {
    "contract": "0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "contract_name": "Address",
    "contract_link": "https://etherscan.io/address/0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "uuid": "b272ee6e-1e51-45ba-82d5-880b8bee01aa",
    "severity": "",
    "sol_function": 
        function _revert(bytes memory returndata, string memory errorMessage) private pure {
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
        },
    "sol_instruction": 
        assembly {
            let returndata_size := mload(returndata)
            revert(add(32, returndata), returndata_size)
        }
  }
]
```
