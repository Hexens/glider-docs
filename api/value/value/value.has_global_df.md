---
description: >-
  Returns true when the value interacts with a global variable such as
  msg.sender, msg.data, etc. from inside the function.
---

# Value.has\_global\_df()

`has_global_df() → bool`

The function traverses the data-flow graph within the current function scope and returns true if the Value interacts with a global variable at any point in its data flow, and false otherwise.

By "interacts," we mean the Value is used in an operation that reads or writes a global variable, or is combined with a value derived from a global. For example, if we analyze the lastDatasetId value, the following counts as an interaction because lastDatasetId is used to access the global mapping datasetOwners:

`datasetOwners[lastDatasetId] = msg.sender;`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Functions()
        .with_name("registerDatasetProfile")
        .exec(1)
        .instructions()
        .exec(2)
    )

    for instruction in instructions:
        components = instruction.get_components()
        for component in components:
            print("Value: " + component.expression)
            print("Contains global df: ", component.has_global_df())

    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-04 at 12.37.08 PM.png" alt=""><figcaption></figcaption></figure>
