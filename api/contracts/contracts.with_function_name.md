---
description: Adds a filter to get contracts that have a function with the given name.
---

# Contracts.with\_function\_name()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_function_name('setAdmin').exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0xdD1fdeE333377b490e63e8090Ac80E4BC6Aa0965",
    "0xb5F03971509F2Ddb0a9D5Fd5c147D8FE630a6886",
    "0x912A5C85335b664cD6D08B55b94ACF01bb878FA6",
    "0xbb1cae40e6d872885392657c16701bb1435c82c4",
    "0x97Ff2B98069A255537b9f3b44A991236895f3401"
  ]
}
```
