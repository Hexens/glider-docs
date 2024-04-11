---
description: Returns true if the first type can be converted to the second.
---

# Convertor.can\_convert()

**`can_convert`**`(`_`from_type: str`_`,`` `_`to_type: str`_`) → bool`



```python
from glider import *

def query():
  # Create a Convertor object 
  convertor = Convertor()

  # Add a conversion from address to bytes20
  convertor.add("address", "bytes20")

  # Returns true
  print(convertor.can_convert("address", "bytes20"))

  # Returns false as conversion from address to uint160 was not added
  print(convertor.can_convert("address", "uint160"))

  return []
```

Output:

```json
{
  "print_output": [
    "True",
    "False"
  ]
}
```
