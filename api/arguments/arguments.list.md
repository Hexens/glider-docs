---
description: >-
  Returns a list of all the arguments that are passed as parameters to the
  function.
---

# Arguments.list()

`list() -> List[`[`Argument`](../argument/)`]`

## Example Query

```python
from glider import *


def query():
  functions = Functions().exec(100)

  for f in functions:
    # list() converts the arguments into a list that we can iterate through
    for arg in f.arguments().list():
      print(f"Argument source code: {arg.get_variable().data}")

  return []
```

Example of a ERC721 transferFrom function with 3 arguments&#x20;

ERC721.transferFrom(address from ,address to ,uint256 tokenId)

## Output Example

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
