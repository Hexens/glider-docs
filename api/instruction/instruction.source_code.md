---
description: Returns the source code of the instruction
---

# Instruction.source\_code()

## Query Example

```python
from glider import *
def query():

  instructions = Instructions().exec(1,1)

  print(instructions[0].source_code())
  
  return instructions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (207).png" alt=""><figcaption></figcaption></figure>
