---
description: Adds a filter to get contracts that are main.
---

# Contracts.mains()

The engine marks the contract as main, that is the one being executed on the deployed address

## Query Example

```python
from glider import *

def query():

  main_contracts = Contracts().mains().exec(5)

  return main_contracts
```

## Output Example

```python
{
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
        "contract_name": "Token"
    }, 
    {
        "contract": "0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c",
        "contract_name": "AirdropNFTs"
    },
    {
        "contract": "0x23297ee054e8f600af482013ddbe856b7178a7d3",
        "contract_name": "ZeroExV3ExchangeWrapper",
    },
    {
        "contract": "0x5e6b2027f794a069bfa5e80195e22544d40ae600",
        "contract_name": "NATEHALLINAN"
    },
    {
        "contract": "0xf771d1456b681a37e64b789098615a28279968eb",
        "contract_name": "BOXIMATOR"
    }
}
```
