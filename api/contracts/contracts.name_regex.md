---
description: Adds a filter to get contracts whose names match the given regex.
---

# Contracts.with\_name\_regex()

`with_name_regex(`_`regex: str`_`) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():

  non_interface_contract = Contracts().with_name_regex('^[^I][^A-Z].*').exec(1)

  return non_interface_contract
```

## Output Example

<figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>
