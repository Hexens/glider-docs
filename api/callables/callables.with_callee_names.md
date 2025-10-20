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
  # Retrieve all functions that call both the owner() and msgSender() functions
  functions = Functions().with_callee_names(["owner", "msgSender"]).exec(1)

  # Returns the function found
  return functions
```

## Example Output

```solidity
constructor () {
    _balances[_msgSender()] = 10000;
    _isExcludedFromFee[owner()] = true;
}
```

## Modifier Example

```python
from glider import *


def query():
  # Retrieve all the modifiers that call both the owner() and msgSender() functions
  modifiers = Modifiers().with_callee_names(["owner", "msgSender"]).exec(1)

  # Return the modifier found
  return modifiers
```

## Example Output

```solidity
modifier onlyOwner() {
    require(owner() == _msgSender(), "Ownable: caller is not the owner");
    _;
}
```

