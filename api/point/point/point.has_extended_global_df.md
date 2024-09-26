---
description: >-
  Returns true if the point has a dependency on external variables in the
  current data flow graph and outside of that, false otherwise.
---

# Point.has\_extended\_global\_df()

`has_extended_global_df() → bool`

## Query Example

```python
from glider import *


def query():
  instructions_extended = (
    Instructions()
    .exec(10, 10)
    .filter(lambda x: x.has_extended_global_df())
  )

  print(len(instructions_extended))

  return instructions_extended
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

## has\_extended\_global\_df vs has\_global\_df

Let's dive into the difference between `has_extended_global_df()` and `has_global_df()`.

The function `has_extended_global_df()` works recursively, whereas `has_global_df()` does not. In the previous example, as well as in the example using `has_global_df()`, no significant differences were observed. However, in the example below, we can clearly see the distinction between the two functions.

The following query demonstrates the difference: `has_global_df()` returns `259` instructions, while `has_extended_global_df()` returns `261` instructions.

### Here is a query to highlight the difference:

```python
from glider import *


def query():
  instructions_extended = ( # 261
    Instructions()
    .exec(500)
    .filter(lambda x: x.has_extended_global_df())
  )

  foo1 = set(instructions_extended)

  instructions = ( # 259
    Instructions()
    .exec(500)
    .filter(lambda x: x.has_global_df())
  )

  foo2 = set(instructions)

  res = []

  difference = foo1 - foo2

  for ins in difference:
    res.append(ins)

  return res

```

### Here is the output

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
