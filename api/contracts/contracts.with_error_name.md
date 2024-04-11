---
description: Adds a filter to get contracts that have an error with the given name.
---

# Contracts.with\_error\_name()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_error_name("Invalid").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x97e121ecdcf554f60857e5dc39ed1ea14337d506",
    "0x97e121ecdcf554f60857e5dc39ed1ea14337d506",
    "0x87B80d07efCC64F19Bf873Dc87A99c85E591036b",
    "0x9eb83e11c9a6a15a9aee8f65cc69d205dc3f3fa5",
    "0xee16846aee123e32cf3baa9ee17121e92abc174c"
  ]
}
```
