---
description: Returns a list of arguments having specified name
---

# Arguments.with\_name()

`with_name(arg_name: str, sensitivity: bool = False) -> List[`[`Argument`](../argument/)`]`



## Query Example

```python
def query():
  functions = Contracts().non_interface_contracts().functions().exec(25)

  function_with_args = []
  for f in functions:
    # Prepare the object for this function
    function = {"Function Name": f.name(), "Arguments": []}

    # For each of its arguments...
    for arg in f.arguments().with_name("account"):
      # ...return the data of the argument with specified argument name
      function["Arguments"].append({"Argument data": arg.data})
      
      if len(function["Arguments"]) > 0:
        function_with_args.append(function)

  return function_with_args
```

## Output Example

```json
{
    "Function Name": "balanceOf",
    "Arguments":[
        "Argument data": {
            "name": "account",
            "canonical_name": "Token.balanceOf(address).account",
            "type": {
                "type": "elementary",
                "name": "address"
            },
            "memory_type": "memory"
        }
    ],    
}
```
