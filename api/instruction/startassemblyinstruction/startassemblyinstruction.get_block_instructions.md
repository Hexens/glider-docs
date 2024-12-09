---
description: Returns all instructions from the assembly block
---

# StartAssemblyInstruction.get\_block\_instructions()

`get_block_instructions() →` [`APIList`](../../iterables/apilist.md)`[`[`Instruction`](../)`]`

## Query Example

```python
from glider import *

def query():
    assembly_instructions = Functions().exec(1,57).start_asm_instructions().exec()

    for inst in assembly_instructions:
        for block_inst in inst.get_block_instructions():
            print(block_inst.source_code())

    return assembly_instructions
```

## Example Output

```solidity
[
  {
    "contract": "0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "contract_name": "Address",
    "contract_link": "https://etherscan.io/address/0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "uuid": "00c7e035-626c-4392-92ee-470590d07bff",
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
        }
    "sol_instruction": 
        assembly {
            let returndata_size := mload(returndata)
            revert(add(32, returndata), returndata_size)
        }
  },
  {
    "print_output": [
      returndata_size
      let returndata_size := mload(returndata)
      revert(add(32, returndata), returndata_size)
      assembly {
          let returndata_size := mload(returndata)
          revert(add(32, returndata), returndata_size)
      }
    ]
  }
]
```

