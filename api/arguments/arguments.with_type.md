# Arguments.with\_type()

Returns a list of arguments having specified memory type.

```python
def query():
  functions = Functions().exec(1000)

  function_with_args = []
  for f in functions:
    # Prepare the object for this function
    function = {"Function Name": f.name(), "Arguments": []}

    # For each of its arguments...
    for arg in f.arguments().with_type("bytes32"):
      # ...return the data of the arguent
      function["Arguments"].append({"Argument data": arg.data})
      
      if len(function["Arguments"]) > 0:
        function_with_args.append(function)

  return function_with_args
```

Example of an Argument with the memory type bytes32

Output:

```json
{
  "Function Name": "afterAgreementCreated",
  "Arguments": [
    {
      "Argument data": {
        "name": "_agreementId",
        "name_ssa": "_agreementId_0",
        "canonical_name": "LTP.afterAgreementCreated(ISuperToken,address,bytes32,bytes,bytes,bytes)._agreementId",
        "type": "bytes32",
        "memory_type": "memory"
      }
    }
  ]
}
```
