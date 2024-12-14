---
description: Adds a filter to get contracts that have a struct with the given field name.
---

# Contracts.with\_struct\_field\_name()

`with_struct_field_name(name: str, sensitivity: bool = True) →` [`Contracts`](./)



## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_struct_field_name('balance', sensitivity=False).exec(1)
  structs = contracts[0].structs().exec()
  for struct in structs:
    for struct_field in struct.fields:
      print(struct_field.name)
  
  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>
