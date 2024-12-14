---
description: Adds a filter to get contracts that have a struct with the given fields count.
---

# Contracts.with\_struct\_fields\_count()

`with_struct_fields_count(number: int) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts()
    .with_name("DepositSecurityModule")
    .with_struct_fields_count(2)
    .exec(1))

  structs = contracts[0].structs().exec()
  for struct in structs:
    for struct_field in struct.fields:
      print(struct_field.type)
  
  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>
