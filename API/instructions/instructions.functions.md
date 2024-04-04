# Instructions.functions()

**`functions`**`() →` [`Functions`](../functions/)

Returns [Functions](../functions/) object for the functions of the instructions. Note: The function will return parent functions for those instructions that belong to a function, not to a modifier. To get parent modifiers of that instructions use `modifiers()` method.

## Return type

`→` [`Functions`](../functions/)

```python
from glider import *

def query():
  # Fetch a list of functions of the first 2 instructions
  instructions = Instructions().functions().exec(2)
  
  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Context",
  "sol_function": "function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }"
}
```

This returns only one function as the first 2 instructions both belong to it.
