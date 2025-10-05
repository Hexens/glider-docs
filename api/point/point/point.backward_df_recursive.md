---
description: >-
  Returns the list of all previous points of the current point in the current
  data flow graph and outside of that.
---

# Point.backward\_df\_recursive()

`backward_df_recursive() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](./)`]`

## Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_name("_burn")
    .exec(10)
    .filter(
      lambda function : function.get_contract().address() == "0x0B79318ecc4cc8F314A985Fc2Da98891EFd238Bc" and function.get_contract().name == "ERC20Named"
    )
  )

  instructions = functions.instructions().exec(1,1)
  for instruction in instructions:
    backward_dfs = instruction.backward_df_recursive()
    if len(backward_dfs) > 3 and len(backward_dfs) < 7:
      print(f"Count of Points returned by backward_dfs: {len(backward_dfs)}")
      for backward_df in backward_dfs:
        print(backward_df.source_code())
      
  return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 4.48.53 PM.png" alt=""><figcaption></figcaption></figure>

To clarify, what is the difference between `backward_df` and `backward_df_recursive`? `backward_df_recursive` operates recursively. Below is the output when `backward_df` was used instead of `backward_df_recursive` :

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 5.21.42 PM.png" alt=""><figcaption></figcaption></figure>

