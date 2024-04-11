# Function.modifiers()

Returns the [Modifiers](../modifiers/) object for the modifiers of the function.

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(100)

  # Retrieve the modifiers of the first function
  modifers = functions[0].modifiers().exec();

  return modifers
```

\


Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_modifier": "modifier onlyOwner() {\n        require(owner() == _msgSender(),\"Ownable: caller is not the owner\");\n        _;\n    }"
}
```
