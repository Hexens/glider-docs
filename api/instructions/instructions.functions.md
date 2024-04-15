---
description: >-
  Returns Functions object for the functions of the instructions. Note: The
  function will return parent functions for those instructions that belong to a
  function, not to a modifier. To get parent modif
---

# Instructions.functions()

**`functions`**`() →` [`Functions`](../functions/)

## Return type

`→` [`Functions`](../functions/)

## Query Example

```python
from glider import *

def query():
  # Fetch a list of functions of the first instructions
  instructions = Instructions().functions().exec(1)
  
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
}
```
