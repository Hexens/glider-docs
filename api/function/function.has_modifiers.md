---
description: Returns true if the function has modifiers, otherwise returns false
---

# Function.has\_modifiers()

`has_modifiers() → bool`

## Example

```python
from glider import *

def query():
  # Retrieve a function with name _afterTokenTransfer
  functions = Functions().with_name('_afterTokenTransfer').exec(1)
  for function in functions:
    print(function.has_modifiers())

  return []
```

## Output

```json
"root":{1 item
"print_output":[1 item
0:string"False"
]
}
```

