---
description: >-
  Adds a filter to get instructions that call a function with the given
  signature.
---

# Instructions.with\_callee\_signature()

`with_callee_signature(signature: str) →` [`Instructions`](./)

## Query Example

```python
from glider import *


def query():
  return (
    Instructions()
    .with_callee_signature("deposit(uint256)")
    .exec(2,12)
  )
```

## Example Output

<figure><img src="../../.gitbook/assets/image (270).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (269).png" alt=""><figcaption></figcaption></figure>
