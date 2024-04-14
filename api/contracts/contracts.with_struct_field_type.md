---
description: Adds a filter to get contracts that have a struct with the given field type.
---

# Contracts.with\_struct\_field\_type()

## Function Signature

`with_struct_field_type(field_type: str, sensitivity: bool = True) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts().
    with_name("DepositSecurityModule").
    with_struct_field_type('bytes32').
    exec(1)
  )
  
  return contracts
```

## Output Example

```python
{
    {
        "contract": "0xdb149235b6f40dc08810aa69869783be101790e7",
        "contract_name": "DepositSecurityModule"
    }
}
```
