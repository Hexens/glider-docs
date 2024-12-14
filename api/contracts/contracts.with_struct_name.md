---
description: Adds a filter to get contracts that have a struct with the given name.
---

# Contracts.with\_struct\_name()

`with_struct_name(name: str, sensitivity: bool = True) →` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = (
    Contracts()
    .with_struct_name("User")
    .exec(1))

  structs = contracts[0].structs().exec()
  for struct in structs:
      print(struct.name)
  
  return contracts
```

## Output Example

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

