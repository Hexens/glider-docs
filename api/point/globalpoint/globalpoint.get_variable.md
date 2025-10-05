---
description: Abstract method that returns object of variable
---

# GlobalPoint.get\_variable()

`get_variable() →` [`GlobalVariable`](../../variables/globalvariables.md)

## Query Example

```python
from glider import *


def query():
    instructions = (
        Functions()
        .with_name("_msgSender")
        .exec(1)
        .instructions()
        .exec()
    )

    dfs = instructions.backward_df()
    for df in dfs:
      print(df.get_variable())
      print(df.source_code())

    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 10.52.07 AM.png" alt=""><figcaption></figcaption></figure>
