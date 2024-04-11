---
description: >-
  Returns a list of Call objects that represents called functions from the
  function/modifier.
---

# Callable.callee\_values()

## Return type

→ List\[[Call](../callnode/)]

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  results = []
  for function in functions:
    for call in function.callee_values():
      # Return the expression (code) of each call in each function
      results.append({"function": function.name(), "call": call.expression})

  return results
```

## Example output

```json
[
  {
    "function": "transferOwnership",
    "call": "require(bool,string)(newOwner != address(0),\"Ownable: new owner is the zero address\")"
  },
  {
    "function": "transferOwnership",
    "call": "_setOwner(newOwner)"
  },
  ...
]
```
