---
description: Returns a list of the functions calls instructions
---

# Instructions.low\_level\_external\_calls()

`low_level_function_calls() →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return Instructions().low_level_external_calls().exec(3)
```

## Example Output

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
