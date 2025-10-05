---
description: Executes the formed query and returns the list of Instruction objects
---

# Instructions.exec()

`exec(limit_count: int = 0, offset_count: int = 0) →` [`APIList`](../iterables/apilist.md)`[`[`Instruction`](../instruction/)`]`

`limit_count` is the number of instructions to query, while `offset_count` is the offset applied to the results returned. For example with `offset_count` = 2, will return `limit_count` instructions starting from the 3rd instructions.

## Query Example

```python
from glider import *


def query():
  return Instructions().exec(10)
```

## Example Output

<figure><img src="../../.gitbook/assets/image (251).png" alt=""><figcaption></figcaption></figure>
