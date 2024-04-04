# Instructions.with\_called\_function\_name\_prefix()

**`with_called_function_name_prefix`**`(`_`prefix: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Instructions`](./)

Adds a filter to get instructions that call a function whose name has the given prefix.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of intructions that call a function or modifier with prefix "only"
  instructions = Instructions().with_called_function_name_prefix("only").exec(1)

  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": function renounceOwnership() public virtual onlyOwner {
        _setOwner(address(0));
    },
  "sol_instruction": onlyOwner
}
```
