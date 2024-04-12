---
description: Adds a filter to get contracts that have an error with the given signature.
---

# Contracts.with\_error\_signature()

## Function Signature

`with_error_signature(signature: str) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts().
    with_error_signature('InsufficientBalance(uint256,uint256)').
    exec(1)
    )

  return contracts
```

## Output Example

```python
{
    {
        "contract": "0x3e2c366065ba0f6f9936c2c6a802d72f250b27aa",
        "contract_name": "Address"
    }
}
```
