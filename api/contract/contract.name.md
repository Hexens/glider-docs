---
description: Returns the name of a Contract.
---

# Contract.name

_`property`_` ``name`_`: str`_

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(5)
  
  names = []
  for contract in contracts:
    names.append(contract.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "Context",
    "Ownable",
    "IERC165",
    "ERC165",
    "IERC721"
  ]
}
```
