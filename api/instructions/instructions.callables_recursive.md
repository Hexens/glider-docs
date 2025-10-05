---
description: >-
  Returns a set of Callables objects for the callables where the instructions
  can be executed in.
---

# Instructions.callables\_recursive()

`callables_recursive() →` [`APISet`](../iterables/apiset.md)`[`[`Callables`](../callables/)`]`&#x20;

Consider the following Solidity code:

```solidity
modifier onlyOwner() {
        require(_owner == _msgSender(),"Ownable: caller is not the owner");
        _;
}

function includeInFee(address account) public onlyOwner {
        _isExcludedFromFee[account] = false;
}
```

For the following instruction:

```solidity
_isExcludedFromFee[account] = false;
```

Both the `includeInFee` function and `onlyOwner` modifier can call the instruction above. &#x20;

With `callables_recursive()`, one can retrieve the functions that are called recursively through the entire call chain.

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
        .callables_recursive()
        .exec()
        .name
    )

    return functions
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-18 at 9.41.40 AM.png" alt=""><figcaption></figcaption></figure>
