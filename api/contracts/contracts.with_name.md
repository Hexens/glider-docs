---
description: Adds a filter to get contracts with the given name.
---

# Contracts.with\_name()

## Function Signature

`with_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_name("Deposit", sensitivity=False).exec(1)
  
  return contracts
```

## Output Example

```json
{
    {
        "contract": "0xad23d386ff5be971fcf57f34f477217f91bbc44d",
        "contract_name": "Deposit"
    }
}
```
