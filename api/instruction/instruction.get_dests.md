---
description: >-
  Returns the list of Value objects representing the destination(s) of the
  instruction. This function returns the list to accommodate cases like 'a= b =
  c= 5', where the destinations are [a, b, c].
---

# Instruction.get\_dests()

`get_dests() → APIList[`[`Value`](../value/) `|` [`NoneObject`](../internal/noneobject/)`]`&#x20;

## Query Example

```python
from glider import *


def query():
  instruction = Instructions().exec(1,1)
  dests = instruction[0].get_dests()
  
  for dest in dests:
    print(dest.expression)
      
  return [instruction[0]]
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-03 at 11.44.21 AM.png" alt=""><figcaption></figcaption></figure>
