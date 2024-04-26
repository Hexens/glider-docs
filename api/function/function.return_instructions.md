# Function.return\_instructions()

`return_instructions() →` [`Instructions`](../instructions/)

Returns the `return` instructions of the function.

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(10)

  # Retrieve the return instructions of the first function
  instruction = functions[0].return_instructions().exec()

  return instruction
```

\


Output:

```solidity
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Context"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
"sol_instruction":solidity
return msg.sender
}
```
