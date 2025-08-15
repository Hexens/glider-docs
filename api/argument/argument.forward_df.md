---
description: >-
  Returns a list of all instructions following the current point in the current
  data flow graph.
---

# Argument.forward\_df()

`forward_df() → List[`[`Instruction`](../instruction/)`]`

## Example Query

```python
from glider import *
def query():
    func = Contracts().non_interface_contracts().functions().with_arg_count(1).exec(1, 1)[0]
    instrs = []
    for ins in func.arguments().list()[0].forward_df():
        instrs.append(ins)
    return instrs
```

## Output Example

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-23 at 12.32.45 PM.png" alt=""><figcaption></figcaption></figure>
