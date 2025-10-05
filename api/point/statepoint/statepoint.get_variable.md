---
description: Method that returns object of variable
---

# StatePoint.get\_variable()

`get_variable() →` [`StateVariable`](../../variables/statevariables/statevariable.md)

## Query Example

```python
from glider import *


def query():
    instructions = (
        Functions()
        .with_name("latestRoundData")
        .exec(1)
        .instructions()
        .exec()
    )

    for instruction in instructions:
      for df in instruction.get_components():
        if isinstance(df, VarValue):
          for state_point in df.get_defining_points():
            print(state_point.get_variable())
 

    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-10 at 1.55.48 PM.png" alt=""><figcaption></figcaption></figure>
