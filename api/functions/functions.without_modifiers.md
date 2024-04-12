# Functions.without\_modifiers()

`without_modifiers() →` [`Functions`](./)

Adds a filter to get functions that don't have modifiers at all.

## Example

```python
from glider import *

def query():
  functions = Functions().without_modifiers().exec(1)

  return functions
```

## Output

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Context"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
}
```
