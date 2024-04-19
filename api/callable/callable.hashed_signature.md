---
description: >-
  Returns the selector (4 bytes of keccak256 hash) of the function's or
  modifier's signature.
---

# Callable.hashed\_signature()

`hashed_signature() → int`

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  functions_with_sig = []
  for function in functions:
    functions_with_sig.append({"function": function.name(), "sig": function.hashed_signature()})

  return functions_with_sig
```

## Example output

```json
[
  {
    "function": "ownerOf",
    "sig": 1666326814
  },
  {
    "function": "balanceOf",
    "sig": 1889567281
  },
  {
    "function": "transferFrom",
    "sig": 599290589
  },
  ...
]
```
