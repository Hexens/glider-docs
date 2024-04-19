---
description: Adds a filter to get contracts that have a struct with the given fields count.
---

# Contracts.with\_struct\_fields\_count()

`with_struct_fields_count(number: int) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts().
    with_name("DepositSecurityModule").
    with_struct_fields_count(2).
    exec(1)
  )
  
  return contracts
```

## Output Example

```json
{
    {
        "contract": "0xdb149235b6f40dc08810aa69869783be101790e7"
        "contract_name": "DepositSecurityModule"
    }
}
```
