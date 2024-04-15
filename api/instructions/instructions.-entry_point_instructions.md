---
description: Returns an Instructions object for the 'entry point' instructions
---

# Instructions. entry\_point\_instructions()

`entry_point_instructions() →` [`Instructions`](./)

The [Instructions](./) object returned includes all entry points to functions.

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  # Fetch a list of entry point instructions
  instructions = Instructions().entry_point_instructions().exec(1)
  
  return instructions
```

## Output Example

```solidity
{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
    "contract_name": "Context"
    "sol_function":
        function _msgSender() internal view virtual returns (address) {
                return msg.sender;
            }
    "sol_instruction":
    {
            return msg.sender;
    }
}
```

As this returns the entry point to the function, the "sol\_instruction" field contains the function body.
