# IfInstruction.get\_condition()

`get_condition() →` [`Condition`](condition/)

Returns condition of the if-statement.

## Query Example

```python
from glider import *

def query():
  instructionlist = Instructions().if_instructions().exec(1)
  
  condition = instructionlist[0].get_condition()
  print(condition.is_eq())
  return instructionlist
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (215).png" alt=""><figcaption></figcaption></figure>

