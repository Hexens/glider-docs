---
description: >-
  Returns a list of the previous instructions of the current node in the control
  flow graph.
---

# Instruction.previous\_instructions()

`previous_instructions() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](./)`]`

The difference between the previous\_instructions() function and [previous\_instruction()](instruction.previous_instruction.md) is that this function will return all previous instructions of the current instruction in the CFG (control-flow-graph).

_The function is intra-procedural, and thus will not follow function calls; for the **inter**-procedural variant of this function, use extended\_previous\_instructions()._

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
return c;
```

the function will return the instructions:

```solidity
uint256 c = a - b;
require(b <= a, errorMessage);
*entry_point_instruction*
```

```solidity
require(b <= a, errorMessage);
```

```solidity
*entry_point_instruction*
{
        require(b <= a, errorMessage);
        uint256 c = a - b;

        return c;
}
```

{% hint style="info" %}
Entry point instruction" is a type of instruction that does not exist in real code. It is used internally by the Glider engine
{% endhint %}

## Query Example

```python
from glider import *

def query():
  instructions = Functions().with_name("sub").exec(1,1).instructions().exec(1,3)

  return instructions + list(instructions[0].previous_instructions())
```

## Example Output

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



{% hint style="info" %}
As can be seen from the last output, "virtual" instructions like entry-point instruction, end-if, etc. when being printed with source\_code() will print full code block's source
{% endhint %}

{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
