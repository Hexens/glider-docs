---
description: Returns the function's or modifier's source line numbers.
---

# Callable.source\_line()

## Return type

→ int

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  functions_location = []
  for function in functions:
    # Return the source line number of each function
    functions_location.append({"function": function.name(), "line": function.source_line()})

  return functions_location
```

## Example output

```json
[
  {
    "function": "name",
    "line": 229
  },
  {
    "function": "symbol",
    "line": 234
  },
  {
    "function": "tokenURI",
    "line": 239
  },
  ...
]
```
