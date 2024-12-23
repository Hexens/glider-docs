---
description: Adds a filter to get functions/modifiers having specified callee names.
---

# Callables.with\_callee\_names()

`with_callee_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables that have all of the specified callees (functions that are being called within a function/modifier). Returns a filtered [Callables](./) child object.&#x20;

This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

## Function Example

```python
from glider import *

def query():
  # Retrieve all the modifiers with the signature `nonReentrant()`
  functions = Functions().with_callee_names(["owner", "msgSender"]).exec(1)

  # Return the first five modifiers
  return functions
```

## Output

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

## Modifier Example

```python
from glider import *

def query():
  # Retrieve all the modifiers with the signature `nonReentrant()`
  modifiers = Modifiers().with_callee_names(["owner", "msgSender"]).exec(1)

  # Return the first five modifiers
  return modifiers
```

## Output

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>



