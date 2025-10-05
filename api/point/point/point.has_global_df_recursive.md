---
description: >-
  Returns true if the point has a dependency on external variables in the
  current data flow graph and outside of that, false otherwise.
---

# Point.has\_global\_df\_recursive()

`has_global_df_recursive() → bool`

## Query Example

```python
from glider import *


def query():
  recursive_instructions = (
    Instructions()
    .exec(10, 10)
    .filter(lambda x: x.has_global_df_recursive())
  )

  print(len(recursive_instructions))

  return recursive_instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 9.27.43 AM.png" alt=""><figcaption></figcaption></figure>

## has\_global\_df\_recursive vs has\_global\_df

Let's dive into the difference between `has_global_df_recursive()` and `has_global_df()`.

The function `has_global_df_recursive()` works recursively, whereas `has_global_df()` does not. In the previous example, as well as in the example using `has_global_df()`, no significant differences were observed. However, in the example below, we can clearly see the distinction between the two functions.

The following query demonstrates the difference: `has_global_df()` returns `259` instructions, while `has_global_df_recursive()` returns `261` instructions.

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

### Here is the output:

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
