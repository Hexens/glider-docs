---
description: >-
  Adds a filter to get functions/modifiers that have declarer contract with the
  given name.
---

# Callables.with\_declarer\_contract\_name()

`with_declarer_contract_name(`_`name: str, sensitivity: bool = True`_`) →` [`Callables`](./)

## Function Example

### Example Query

```python
from glider import *


def query():
  # Retrieve the contracts of a list of functions
  contracts = Functions().with_declarer_contract_name("TestToken").exec(2)

  # Return the first five contracts
  return contracts[:5]
```

### Query Output&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-25 at 5.22.26 PM.png" alt=""><figcaption></figcaption></figure>

## Modifier Example

### Example Query

```python
from glider import *


def query():
  # Retrieve the contracts of a list of modifiers
  contracts = Modifiers().with_declarer_contract_name("TestToken").exec(2)

  # Return the first five contracts
  return contracts[:5]
```

### Query Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-25 at 5.19.25 PM.png" alt=""><figcaption></figcaption></figure>
