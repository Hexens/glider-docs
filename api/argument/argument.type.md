---
description: Returns the type of the argument.
---

# Argument.type

## Return Type:

* Type

```python
from glider import *
def query():
  functions = Functions().with_arg_count(2).exec(1)

  function_with_args = []
  for f in functions:
    # Prepare the object for this function
    function = {"Function Name": f.name(), "Arguments": []}

    # For each of its arguments...
    for arg in f.arguments().list():
      # ...return the data of the argument
      function["Arguments"].append({"Argument type": arg.type.name})
      function_with_args.append(function)

  return function_with_args
```

## Output:

```json
"root":{2 items
"Function Name":string"transfer"
"Arguments":[2 items
0:{1 item
"Argument type":string"address"
}
1:{1 item
"Argument type":string"uint256"
}

```
