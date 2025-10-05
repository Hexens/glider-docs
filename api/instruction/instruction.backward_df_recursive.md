---
description: >-
  Returns the list of all previous points of the current point in the current
  data flow graph and outside of that.
---

# Instruction.backward\_df\_recursive()

`backward_df_recursive() →` [`APISet`](../iterables/apiset.md)`[`[`Point`](../point/)`]`

The function works similarly to [Instruction.backward\_df()](instruction.backward_df.md); the main difference is that in case of Instruction.backward\_df() the function will return backward dataflow point for every point in the Instruction, while Instruction.backward\_df() returns only those connected with the current Instruction.&#x20;

Like all other dataflow (DF) functions, it returns a list/set of Points, which can be instructions or "points" in the code, such as arguments, variables, etc.

## Query Example

```python
from glider import *


def query():
  # Fetch an instruction
  instructions = Instructions().with_callee_name('verify').exec(1)
  
  for points in instructions[0].backward_df_recursive():
    print(points.source_code())

  # Return the list of previous instructions of the current instruction
  return instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-17 at 1.41.25 PM.png" alt=""><figcaption></figcaption></figure>
