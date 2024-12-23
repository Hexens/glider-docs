---
description: >-
  Adds a filter to get functions/modifiers that have declarer contract with the
  given name.
---

# Callables.with\_declarer\_contract\_name()

`with_declarer_contract_name(`_`name: str, sensitivity: bool = True`_`) →` [`Callables`](./)

## Function Example

```python
from glider import *

def query():
  functions = Functions().with_declarer_contract_name("OFTCoreUpgradeable").exec(10)

  return functions
```

## Output&#x20;

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

## Modifier Example

```python
from glider import *

def query():
  functions = Modifiers().with_declarer_contract_name("Ownable").exec(10)

  return functions
```

## Output

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
