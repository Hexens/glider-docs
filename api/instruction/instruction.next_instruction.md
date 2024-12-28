---
description: Returns a list of immediate following instructions in the control flow graph.
---

# Instruction.next\_instruction()

`next_instruction() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](./)`]`

The difference between the next\_instruction() function and [next\_instructions()](instruction.next_instructions.md) is that this function will return a list of instructions that are immediately following the current instruction in the CFG (control-flow-graph).



_The function operates non-recursively, meaning it works intra-procedurally._



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

the function will return the instruction:

```solidity
require(c >= a, "SafeMath: addition overflow");
```

## Query Example

```python
from glider import *
def query():
  instructions = Functions().with_name("sub").exec(1,1).instructions().exec(1,1)

  return instructions + instructions[0].next_instruction()
```

## Example Output

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

