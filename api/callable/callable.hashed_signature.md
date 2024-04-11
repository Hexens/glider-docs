---
description: Returns keccak256 hash of the function's or modifier's signature.
---

# Callable.hashed\_signature()

## Return type

→ int

## Example

```python
from glider import *
def query():
  functions = Functions().with_modifiers_name_not(["onlyOwner"]).exec(100)

  functions_with_sig = []
  for function in functions:
    # For each function without an "onlyOwner" modifier, return the hashed signature
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
