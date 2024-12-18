---
description: Returns break instructions of the function/modifier.
---

# Callable.break\_instructions()

`break_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  results = []
  for function in functions:
    # For each function, return each break instruction
    for instruction in function.break_instructions().exec():
      results.append(instruction)

  return results
```

## Example output

<figure><img src="../../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>
