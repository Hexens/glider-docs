---
description: Returns the source code of the argument.
---

# Argument.source\_code()

`source_code() → str`



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
      function["Arguments"].append({"Argument Source code": arg.source_code()})
      function_with_args.append(function)

  return function_with_args
  
```

Output:

```json
{
  "Function Name": "approve",
  "Arguments": [
    {
      "Argument Source code": "address to"
    },
    {
      "Argument Source code": "uint256 tokenId"
    }
  ]
}
```
