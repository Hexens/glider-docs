# Functions.exec()

`exec(`_`limit_count: int = 0`_`,`` `_`offset_count: int = 0`_`) → List[`[`Function`](../function/)`]`

Executes the formed query and returns a list of the Function objects.

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(2)

  return functions
```



Output:

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": "function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }"
  }
]
```
