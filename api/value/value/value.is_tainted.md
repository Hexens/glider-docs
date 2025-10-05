---
description: Returns whether the value is tainted.
---

# Value.is\_tainted()

## Query Example

Consider the following Solidity function:

```solidity
function _transfer(address from,address to,uint256 amount) private {
    require(from != address(0),"ERC20: transfer from the zero address");
    require(amount > 0,"Transfer amount must be greater than zero");
    emit record(from,to); 

    // Emitted code for brevity
}
```

In this function, we want to determine if the following line is influenced by user input:

```solidity
require(from != address(0),"ERC20: transfer from the zero address");
```

We know that `from` comes from a function argument, which is user-controlled. Therefore, this line of code is influenced by user input, and therefore tainted.

To write a query to confirm this, we first query the components in the instruction and call `is_tainted()` against any of the Values.

```python
from glider import *


def query():    
    return (
        Contracts()
        .with_name("aa2Token")
        .exec(1)
        .functions()
        .with_name("_transfer")
        .exec(1)
        .instructions()
        .exec(2)
        .filter(is_tainted)
    )

def is_tainted(instruction):
    components = instruction.get_components()
    
    for component in components:
        if component.is_tainted():
            return True

    return False
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-16 at 6.36.15 PM.png" alt=""><figcaption></figcaption></figure>
