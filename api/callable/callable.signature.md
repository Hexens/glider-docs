---
description: Returns the function's or modifier's signature.
---

# Callable.signature()

## Return type

→ str

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  functions_with_sig = []
  for function in functions:
    # Aggregate the signature of each function along with their name
    functions_with_sig.append({"function": function.name(), "sig": function.signature()})

  return functions_with_sig
```

## Example output

```json
[
  {
    "function": "transferOwnership",
    "sig": "transferOwnership(address)"
  },
  {
    "function": "safeTransferFrom",
    "sig": "safeTransferFrom(address,address,uint256)"
  },
  ...
]
```
