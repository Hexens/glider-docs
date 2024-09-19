---
description: Adds a filter to get contracts that names have the given suffix.
---

# Contracts.with\_name\_suffix()

`with_name_suffix(`_`suffix: str, sensitivity: bool = True`_`) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():

  prefix_contracts = Contracts().with_name_suffix("link", sensitivity=False).exec(1)

  return prefix_contracts
```

## Output Example

```python
{
    {
        "contract": "0xc8d60d8273e69e63eafc4ea342f96ad593a4ba10",
        "contract_name": "CalculationsChainlink"
    }
}
```
