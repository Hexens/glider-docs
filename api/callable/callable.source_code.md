---
description: Returns the source code of the function/modifier.
---

# Callable.source\_code()

## Return type

→ str

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  functions_code = []
  for function in functions:
    # Aggregate the code of each function along with their name
    functions_code.append({"function": function.name(), "code": function.source_code()})

  return functions_code
```

## Example output

```json
[
  {
    "function": "_msgSender",
    "code": `
    // Formatted for the example
    function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
    `
  },
  {
    "function": "renounceOwnership",
    "code": `
    // Formatted for the example
    function renounceOwnership() public virtual onlyOwner {
        _setOwner(address(0));
    }
    `
  },
  ...
]
```
