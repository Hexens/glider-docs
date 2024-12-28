---
description: Returns a list of all high level static call instructions.
---

# Instructions.high\_level\_static\_calls()

`high_level_static_calls() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():

  return Instructions().high_level_static_calls().exec(1, 5)
```

## Output Example

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

In this instance, the static call refers to `uniswapV2Router.WETH()`.
