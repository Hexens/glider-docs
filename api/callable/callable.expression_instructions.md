---
description: Returns expression instructions of the function/modifier.
---

# Callable.expression\_instructions()

`expression_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  expressions = []
  for function in functions:
    for exp_instruction in function.expression_instructions().exec():
      # For each function, return the expressions
      expressions.append(exp_instruction)

  return expressions
```

## Example output

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>
