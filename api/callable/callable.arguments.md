---
description: Returns an Arguments object for the arguments of the function/modifier.
---

# Callable.arguments()

## Return type

→ [Arguments](../arguments/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  function_with_args = []
  for f in functions:
    # Prepare the object for this function
    function = {"function": f.name(), "args": []}

    # For each of its arguments...
    for arg in f.arguments().list():
      # ...return the type and name
      function["args"].append({"type": arg.type, "name": arg.name})

    # Add the function to the array only if it has at least one argument
    if len(function["args"]) > 0:
      function_with_args.append(function)

  return function_with_args
```

## Example output

```json
[
  {
    "function": "approve",
    "args": [
      {
        "type": "address",
        "name": "to"
      },
      {
        "type": "uint256",
        "name": "tokenId"
      }
    ]
  },
  ...
]
```
