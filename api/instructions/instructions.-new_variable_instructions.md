---
description: Returns an Instructions object for the new variable creation instructions
---

# Instructions.new\_variable\_instructions()

`new_variable_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return Instructions().new_variable_instructions().exec(2,3)
```

## Example Output

<figure><img src="../../.gitbook/assets/image (204).png" alt=""><figcaption></figcaption></figure>
