---
description: >-
  Returns true when the value interacts with a global variable such as
  msg.sender, msg.data, etc. across multiple functions.
---

# Value.has\_global\_df\_recursive()

`has_global_df_recursive() → bool`

The function is the _**recursive**_**/**_**inter-procedural**_ variant of `has_global_df()`. It traverses the data-flow graph across function boundaries and returns true if the Value interacts with a global variable at any point in its data flow, and false otherwise.

By "interacts," we mean the Value is used in an operation that reads or writes a global variable, or is combined with a value derived from a global. For example, if we analyze the lastDatasetId value, the following counts as an interaction because lastDatasetId is used to access the global mapping datasetOwners:

`datasetOwners[lastDatasetId] = msg.sender;`

The difference between `has_global_df_recursive()` and `has_global_df()` is scope: the non-recursive version analyzes only the current function, while `has_global_df_recursive()` follows the Value’s data flow recursively (across calls) until it either finds an interaction with a global variable or exhausts the flow.

## Query Example

```python
from glider import *

def query():
    instructions = (
        Functions()
        .with_signature("approve(address,uint256)")
        .exec(100)
        .filter(lambda function : function.get_contract().name == "ERC20")[0]
        .instructions()
        .exec()
    )

    for instruction in instructions:
        components = instruction.get_components()
        for component in components:
            if component.has_global_df_recursive():
                print("Value: " + component.expression)

    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-04 at 2.24.53 PM.png" alt=""><figcaption></figcaption></figure>
