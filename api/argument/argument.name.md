---
description: Returns the name of the argument.
---

# Argument.name

_`property`_` ``name`_`: str`_



```python
def query():
  functions = Functions().exec(100)

  function_with_args = []
  for f in functions:
    # Prepare the object for this function
    function = {"Function Name": f.name(), "Arguments": []}

    # For each of its arguments...
    for arg in f.arguments().list():
      # ...return the data of the argument
      function["Arguments"].append({"Argument Name": arg.name})
      function_with_args.append(function)

  return function_with_args
```

Output:

```json
{
  "Function Name": "transferOwnership",
  "Arguments": [
    {
      "Argument Name": "newOwner"
    }
  ]
}
```
