---
description: >-
  Returns the list of all points following the current point in the current data
  flow graph and outside of that.
---

# Point.forward\_df\_recursive()

`forward_df_recursive() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](./)`]`

## Query Example

```python
from glider import *


def query():
  functions = (
    Functions()
    .with_name("claimTreasuryFundRewards")
    .exec(100)
    .filter(lambda function : function.get_contract().address() == "0xc0961B2A7607418F3a4A3611daB84E43842Dbd44")
  )

  instructions = functions.instructions().exec()
  instruction = instructions[1]
 
  forward_dfs = instruction.forward_df_recursive()
  print(f"Count of Points returned by forward_dfs: {len(forward_dfs)}")

  for forward_df in forward_dfs:
    print(forward_df.source_code())

  return instructions

```

## Output Example

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 5.54.31 PM.png" alt=""><figcaption></figcaption></figure>

To clarify, what is the difference between `forward_df` and `forward_df_recursive`? `forward_df_recursive` operates recursively. Below is the output when `forward_df` was used instead of `forward_df_recursive` :

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 5.55.16 PM.png" alt=""><figcaption></figcaption></figure>
