---
description: >-
  Filter functions/modifiers satisfying the given expression of global
  variables.
---

# Callables.with\_globals()

`with_globals(`_`expr: Any`_`) → Callables`

Returns a list of Callables given a list of [global filters](../filters/globalfilters/).&#x20;

The argument represents an expression of GlobalFilter constants and is a bitmask of flags. For example, to find Functions that call msg.value, we will need to pass in the `GlobalFilters.MSG_VALUE` expression:

```python
Functions().with_globals(GlobalFilters.MSG_VALUE).exec(1)
```

If we want to find Functions that call msg.value _and_ msg.sender, we will need to pass in the `GlobalFilters.MSG_VALUE & GlobalFilters.MSG_SENDER` expression:

```python
Functions().with_globals(GlobalFilters.MSG_VALUE & GlobalFilters.MSG_SENDER).exec(1)
```

If we want to find Functions that call msg.data _but not_ msg.sender, we will need to pass in the following  `GlobalFilters.MSG_DATA & ~GlobalFilters.MSG_SENDER` expression:

```python
Functions().with_globals(GlobalFilters.MSG_DATA & ~GlobalFilters.MSG_SENDER).exec(1)
```

Finally, if we want to find functions that _either_ call msg.sender or tx.origin, we will need to pass in the following `GlobalFilters.TX_ORIGIN | GlobalFilters.MSG_SENDER` expression:

```python
Functions().with_globals(GlobalFilters.TX_ORIGIN | GlobalFilters.MSG_SENDER).exec(1)
```

## Example Query

```python
from glider import *


def query():
  functions = Functions().with_globals(GlobalFilters.TX_ORIGIN).exec(1,2)
  
  return functions
```

## Query Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-28 at 3.03.39 PM.png" alt=""><figcaption></figcaption></figure>
