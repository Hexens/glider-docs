---
description: Adds a filter to get contracts that have a struct with the given field type.
---

# Contracts.with\_struct\_field\_type()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_struct_field_type('bytes32').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output(Takes a while \~30 secs):&#x20;

```python
{
  "addresses": [
    "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
    "0xe90baa4A5fD4fE25443d27e6E2883350a0E67855",
    "0x2d8bE62BF76F5c6962E0E44e93374786F329260c",
    "0x1C3517AFb608610DB403401B7C85929774c3cdd7",
    "0x69fEe260917b62C46EC95D7d2FE59DC827934cdD"
  ]
}
```
