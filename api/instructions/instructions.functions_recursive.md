---
description: >-
  Returns Functions object for the functions where the instructions can be
  executed in.
---

# Instructions.functions\_recursive()

`functions_recursive() →` [`Functions`](../callables/functions/)

Consider the following Solidity code:

```solidity
function includeInFee(address account) public onlyOwner {
        _isExcludedFromFee[account] = false;
}
```

For the following instruction:

```solidity
_isExcludedFromFee[account] = false;
```

The `includeInFee` function can call the instruction above. &#x20;

With `functions_recursive()`, one can retrieve the functions that are called recursively through the entire call chain.

## Query Example

```python
from glider import *

def query():
    # Fetch a function
    functions = (
        Functions()
        .with_name("includeInFee")
        .exec(1)
    )

    print(
        functions
        .instructions()
        .functions_recursive()
        .exec()
        .name
    )

    return functions
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-18 at 9.49.57 AM.png" alt=""><figcaption></figcaption></figure>
