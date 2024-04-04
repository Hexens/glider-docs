# Instructions.modifiers()

**`modifiers`**`() →` [`Modifiers`](../modifiers/)

Returns [Modifiers](../modifiers/) object for the modifiers of the instructions. Note: The function will return parent modifiers for those instructions that belong to a modifier, not to a function. To get parent functions of that instructions use `functions()` method.

## Return type

`→` [`Modifiers`](../modifiers/)

```python
from glider import *

def query():
  # Fetch a list of modifiers of the instructions
  instructions = Instructions().modifiers().exec(1)

  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_modifier": modifier onlyOwner() {
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
}
```
