---
description: >-
  Adds a filter to get functions/modifiers that have declarer contract with the
  given name.
---

# Callables.with\_declarer\_contract\_name()

`with_declarer_contract_name(`_`name: str, sensitivity: bool = True`_`) →` [`Callables`](./)

## Query Example

```python
from glider import *

def query():
  functions = Functions().with_declarer_contract_name("OFTCoreUpgradeable").exec(10)

  return functions
```

## Output Example&#x20;

```solidity
[
  {
    "contract": "0xa63780c48eb181ec85e4e7592191b1c5d54fe1a9",
    "contract_name": "OFTAdapterUpgradeable",
    "contract_link": "https://etherscan.io/address/0xa63780c48eb181ec85e4e7592191b1c5d54fe1a9",
    "uuid": "3fc00fc8-2fdb-43d7-b852-215494ebfed6",
    "severity": "",
    "sol_function": 
      function _getOFTCoreStorage() internal pure returns (OFTCoreStorage storage $) {
        assembly {
          $.slot := OFTCoreStorageLocation
        }
    }
  },
  ...
]
```
