# Instructions.entry\_points()

**`entry_points`**`() →` [`Instructions`](./)

Returns an [Instructions](./) object for the entry\_point instructions.

The [Instructions](./) object returned includes all entry points to functions.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of entry point instructions
  instructions = Instructions().entry_points().exec(1)
  
  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }",
  "sol_instruction": "{
        return msg.sender;
    }"
}
```

As this returns the entry point to the function, the "sol\_instruction" field contains the function body.
