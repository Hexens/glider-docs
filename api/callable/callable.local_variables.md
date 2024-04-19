---
description: return the local variables for the function/modifier.
---

# Callable.local\_variables()

`local_variables() →` [`LocalVariables`](../localvariables/)

Returns a LocalVariables object for the local variables of the function/modifier.

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  local_vars = []
  for function in functions:
    for local_var in function.local_variables().list():
      # Return the try instructions for each function
      local_vars.append({"name": local_var.name})

  return local_vars
```

## Output



```json
"root":{1 item
"name":string"c"
},
"root":{1 item
"name":string"msgSender"
}
...
```
