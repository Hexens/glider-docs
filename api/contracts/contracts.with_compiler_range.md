---
description: >-
  Adds a filter to get contracts whose compilation version is in the given
  range.
---

# Contracts.with\_compiler\_range()

Input:

```python
from glider import *

def query():
  contracts = Contracts().with_compiler_range("0.4.0", "0.8.18").exec(5)
  
  addresses = []
  for contract in contracts:
    addresses.append(contract.address())

  return [{"addresses": addresses}]
```

Output:

```python
{
  "addresses": [
    "0x6f1b14a08410c36ea8a3f3cd367a33f89f75b169",
    "0x6f1b14a08410c36ea8a3f3cd367a33f89f75b169",
    "0x5760Ed11eb738e0Da57ADFAa37Ce7808Bcc8738c",
    "0x52eb5c21391aac589f316667d03bd50bafa6d509",
    "0x52eb5c21391aac589f316667d03bd50bafa6d509"
  ]
}
```
