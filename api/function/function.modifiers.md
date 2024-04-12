---
description: Returns the Modifiers object for the modifiers of the function.
---

# Function.modifiers()

`modifiers() →` [`Modifiers`](../modifiers/)

Returns the [Modifiers](../modifiers/) object for the modifiers of the function.

## Example

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().with_one_property([MethodProp.HAS_MODIFIERS]).exec(1)

  # Retrieve the modifiers of the first function
  modifers = functions[0].modifiers().exec()

  return modifers
```

## Output

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Ownable"
"sol_modifier":solidity
modifier onlyOwner() {
        require(_owner == _msgSender(), "Ownable: caller is not the owner");
        _;
    }
```
