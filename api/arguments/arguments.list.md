---
description: >-
  Returns a list of all the arguments that are passed as parameters to the
  function.
---

# Arguments.list()

## Function Signature

`list() -> List[`[`Argument`](../argument/)`]`

## Example Query

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
      function["Arguments"].append({"Argument data": arg.data})
      function_with_args.append(function)

  return function_with_args
```

Example of a ERC721 transferFrom function with 3 arguments&#x20;

ERC721.transferFrom(address from ,address to ,uint256 tokenId)

## Output example

```json
{
  "Function Name": "transferFrom",
  "Arguments": [
    {
      "Argument data": {
        "name": "from",
        "name_ssa": "from_0",
        "canonical_name": "ERC721.transferFrom(address,address,uint256).from",
        "type": "address",
        "memory_type": "memory"
      }
    },
    {
      "Argument data": {
        "name": "to",
        "name_ssa": "to_0",
        "canonical_name": "ERC721.transferFrom(address,address,uint256).to",
        "type": "address",
        "memory_type": "memory"
      }
    },
    {
      "Argument data": {
        "name": "tokenId",
        "name_ssa": "tokenId_0",
        "canonical_name": "ERC721.transferFrom(address,address,uint256).tokenId",
        "type": "uint256",
        "memory_type": "memory"
      }
    }
  ]
}
```
