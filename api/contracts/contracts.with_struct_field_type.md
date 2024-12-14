---
description: Adds a filter to get contracts that have a struct with the given field type.
---

# Contracts.with\_struct\_field\_type()

`with_struct_field_type(field_type: str, sensitivity: bool = True) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts()
    .with_name("DepositSecurityModule")
    .with_struct_field_type('bytes32')
    .exec(1))

  structs = contracts[0].structs().exec()
  for struct in structs:
    for struct_field in struct.fields:
      print(struct_field.type)
  
  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>
