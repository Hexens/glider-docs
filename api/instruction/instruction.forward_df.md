---
description: >-
  Returns a list of all instructions following the current point in the current
  data flow graph.
---

# Instruction.forward\_df()

`forward_df() →` [`APISet`](../iterables/apiset.md)`[`[`Point`](../point/)`]`

The `forward_df()` function is an intra-procedural analysis function. This means that the function does not operate recursively and instead returns instructions within the current function instruction set.

For example, in the function:&#x20;

```solidity
function mul(uint256 a, uint256 b) internal pure returns (uint256) {
        if (a == 0) {
            return 0;
        }
        uint256 c = a * b;
        require(c / a == b, "SafeMath: multiplication overflow");
        return c;
    }
```

For the instruction `uint256 c = a * b;` the forward data flow will return instructions:

```solidity
require(c / a == b, "SafeMath: multiplication overflow");
return c;
```

The easy way to put this is that it will follow the nodes where the variable `c` is being used directly or indirectly.

## Query Example

```python
from glider import *

def query():
    #fetch an instruction
    instructions = Instructions().exec(1,16)
    # return the list of instructions following the current instruction
  
    return instructions + list(instructions[0].forward_df())
```

## Example Output

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
