---
description: Executes the formed query and returns the list of Contract objects.
---

# Contracts.exec()

`exec(`_`limit_count: int = 0, offset_count: int = 0`_`) ->` [`APIList`](../iterables/apilist.md)`[`[`Contract`](../contract/)`]`

## Example Query 1

```python
from glider import *

def query():
  contracts = Contracts().exec(3)

  return contracts
```

## Output Example 1

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Example Query 2

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 2)

  return contracts
```

## Output Query 2

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
