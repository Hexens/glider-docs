---
description: Returns the unique identifier of the function/modifier.
---

# Callable.db\_id

## Return type

→ str

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  ids = []
  for function in functions:
    # Aggregate the ids of all functions
    ids.append(function.db_id)

  return ids
```

## Example output

```json
[
  "functions/96e8caf747cd59ead8760cead194a8d0",
  "functions/ad2bdc3eb0a637e61c001cd0fb29eb29",
  ...
]
```
