---
description: Adds a filter to get contracts that have a struct with the given field name.
---

# Contracts.with\_struct\_field\_name()

## Function Signature

`with_struct_field_name(name: str, sensitivity: bool = True) →` [`Contracts`](./)



## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_struct_field_name('balance', sensitivity=False).exec(1)
  
  return contracts
```

## Output Example

```python
{
    {
        "contract": "0x6dcc3e57e7583430db0b005e40a05554ff7ad4a8",
        "contract_name": "ERC721A"
    }
}
```
