---
description: Returns the internal data of the Argument
---

# Argument.data

It contains the name, canonical\_name, type, and memory\_type of the Argument.

```python
def query():
  functions = Functions().exec(1,2)

  function_with_args = []
  for f in functions:
    # Prepare the object for this function
    function = {"Function Name": f.name(), "Arguments": []}

    # For each of its arguments...
    for arg in f.arguments().list():
      # ...return the data of the argument
      function["Arguments"].append({"Argument data": arg.data})
      function_with_args.append(function)

  return function_with_args
```

Output:

```json
{
  "Function Name": "balanceOf",
  "Arguments": [
    {
      "Argument data": {
        "name": "account",
        "canonical_name": "IERC20.balanceOf(address).account",
        "type": {
          "type": "elementary",
          "name": "address"
        },
        "memory_type": "memory"
      }
    }
  ]
}
```
