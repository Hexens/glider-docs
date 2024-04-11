# Instructions.with\_called\_function\_name\_not()

**`with_called_function_name_not`**`(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Instructions`](./)

Adds a filter to get instructions that don't call a function with the given name.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of intructions that don't call the "transfer" function
  instructions = Instructions().with_called_function_name_not("transfer").exec(1)

  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": constructor() {
        _setOwner(_msgSender());
    },
  "sol_instruction": _setOwner(_msgSender())
}
```
