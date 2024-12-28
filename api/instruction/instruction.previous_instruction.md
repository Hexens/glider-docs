---
description: Returns a list of immediate previous instructions in the control flow graph.
---

# Instruction.previous\_instruction()

`previous_instruction() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](./)`]`

The difference between the previous\_instruction() function and [previous\_instructions()](instruction.previous_instructions.md) is that this function will return a list of immediate previous instructions of the current instruction in the CFG (control-flow-graph).

_The function is intra-procedural._



For example, in the function:

```solidity
function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b <= a, errorMessage);
        uint256 c = a - b;

        return c;
    }
```

for the instruction:&#x20;

```solidity
uint256 c = a - b;
```

the function will return the instruction:

```solidity
require(b <= a, errorMessage);
```

## Query Example

```python
from glider import *
def query():
  instructions = Functions().with_name("sub").exec(1,1).instructions().exec(1,2)

  return instructions + list(instructions[0].previous_instruction())
```

## Output Example

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
