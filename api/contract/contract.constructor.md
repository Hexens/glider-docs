---
description: Returns the constructor of the contract, if exists.
---

# Contract.constructor()

`constructor() →` [`Function`](../callable/function/) `| NoneObject`

## Example query

```python
from glider import *

def query():
  constructors = (
    Contracts()
    .exec(3)
    .constructor()
    .filter(lambda x: not isinstance(x, NoneObject))
  )

  return constructors
```

Starting with Glider 1.0, you can use functions from [`Contracts`](../contracts/), [`Functions`](../callables/functions/), and [`Instructions`](../instructions/) on [`APIList`](../iterables/apilist.md)`[`[`Contract`](./)`]`, [`APIList`](../iterables/apilist.md)`[`[`Function`](../callable/function/)`]`, and [`APIList`](../iterables/apilist.md)`[`[`Instruction`](../instruction/)`]`. More details are available on the [Glider and Declarative Query Writing](../../glider-and-declarative-query-writing.md) page.

Additionally, the filter function is used to ignore [`NoneObject`](../internal/noneobject/). This occurs because not all contracts have a constructor, which may result in [`NoneObject`](../internal/noneobject/) being returned

## Example output

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
