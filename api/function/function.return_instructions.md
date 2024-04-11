# Function.return\_instructions()

Returns the `return` instructions of the function.

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(10)

  # Retrieve the return instructions of the first function
  instruction = functions[0].return_instructions()

  return instruction
```

\


Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }",
  "sol_instruction": "return msg.sender"
}
```
