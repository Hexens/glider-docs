---
description: >-
  Returns a list of all instructions following the current node in the control
  flow graph.
---

# Instruction.next\_instructions()

`next_instructions() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](./)`]`

The difference between the next\_instructions() function and [next\_instruction()](instruction.next_instruction.md) is that this function will return all instructions following the current instruction in the CFG (control-flow-graph).

_The function is intra-procedural, and thus will not follow function calls; for the **inter**-procedural variant of this function, use extended\_next\_instructions()._



For example, in the function:

```solidity
function add(uint256 a, uint256 b) internal pure returns (uint256) {
    uint256 c = a + b;
    require(c >= a, "SafeMath: addition overflow");

    return c;
  }
```

for the instruction:&#x20;

```solidity
uint256 c = a + b;
```

the function will return the instructions:

```solidity
require(c >= a, "SafeMath: addition overflow");
```

```solidity
return c;
```

### Query Example

```python
from glider import *
def query():
  instructions = Functions().with_name("sub").exec(1,1).instructions().exec(1,1)

  return instructions + list(instructions[0].next_instructions())
```

### Output Example

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
