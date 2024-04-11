---
description: >-
  Adds a filter to get contracts that have an error whose name matches the given
  regex.
---

# Contracts.with\_error\_regex()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_error_regex('^Err.*').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0xd6c4884106ff00e231f7c1626c18700b2cb98456",
    "0xb795987CF22936fBc2cA945FFEEAa49894EAcF84",
    "0xb795987CF22936fBc2cA945FFEEAa49894EAcF84",
    "0xb795987CF22936fBc2cA945FFEEAa49894EAcF84",
    "0xb795987CF22936fBc2cA945FFEEAa49894EAcF84"
  ]
}
```
