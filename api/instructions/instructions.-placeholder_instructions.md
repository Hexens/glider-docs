# Instructions.placeholder\_instructions()

Returns an [Instructions](./) object for the [Modifier](../modifier/) placeholder instructions.

`placeholder_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().placeholder_instructions().exec(1)

  return instructions
```

## Output Example

```solidity
{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
    "contract_name": "Ownable"
    "sol_function":
        modifier onlyOwner() {
            require(_owner == _msgSender(), "Ownable: caller is not the owner");
            _;
        }
    "sol_instruction":
        _
}
```
