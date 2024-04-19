---
description: >-
  Returns Contracts object for the contracts from which contract was inherited
  directly or indirectly.
---

# Contract.base\_contracts()

`base_contracts() →` [`Contracts`](../contracts/)

It returns the [Contracts](../contracts/) object representing the base contracts of a Contract. The function is recursive. See the example.

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 6)
  
  names = []
  for contract in contracts:
    bases = contract.base_contracts().exec()

    for base in bases:
      names.append(base.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "Context",
    "ERC165",
    "IERC165",
    "IERC721",
    "IERC721Metadata"
  ]
}
```

If you add `print(contract.source_code())` to the loop, you will see these contracts in the declaration: `contract ERC721 is Context, ERC165, IERC721, IERC721Metadata`. Note that the function outputs `IERC165`, though it is not directly inherited.
