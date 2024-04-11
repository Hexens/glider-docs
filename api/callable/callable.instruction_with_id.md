---
description: Returns an Instruction object with specified id from function.
---

# Callable.instruction\_with\_id()

## Return type

→ [Instruction](../instruction/)

## Example

```python
from glider import *
def query():
  functions = Functions().with_modifiers_name_not(["onlyOwner"]).exec(100)

  # Return the instruction with a specific id in a function
  return [functions[0].instruction_with_id(1)]
```

## Example output

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": `
    // Formatted for the example
    function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
    `,
    "sol_instruction": "return msg.sender"
  }
]
```
