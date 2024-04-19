---
description: Returns a list of arguments having specified memory type.
---

# Arguments.with\_memory\_type()

`with_memory_type(memory_type: str) -> List[`[`Argument`](../argument/)`]`



## Query Example

```python
def query():
  functions = Functions().exec(45)

  function_with_args = []
  for f in functions:
    # Prepare the object for this function
    function = {"Function Name": f.name(), "Arguments": []}

    # For each of its arguments...
    for arg in f.arguments().with_memory_type("storage"):
      # ...return the data of the arguent
      function["Arguments"].append({"Argument data": arg.data})
      
      if len(function["Arguments"]) > 0:
        function_with_args.append(function)

  return function_with_args
```

Example of an Argument with the memory type storage&#x20;

## Output Example

```json
{
  "Function Name": "current",
  "Arguments": [
    {
      "Argument data": {
        "name": "counter",
        "canonical_name": "Counters.current(Counters.Counter).counter",
        "type": {
          "type": "struct",
          "name": "Counter",
          "relative_filepath": "AirdropNFTs.sol",
          "contract_name": "Counters"
        },
        "memory_type": "storage"
      }
    }
  ]
}
```
