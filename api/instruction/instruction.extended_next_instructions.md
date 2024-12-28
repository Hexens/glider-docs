---
description: >-
  Returns the set of all instructions following the current node in the control
  flow graph.
---

# Instruction.extended\_next\_instructions()

`extended_next_instructions() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](./)`]`

The difference between the extended\_next\_instructions() function and [next\_instructions()](instruction.next_instructions.md) is that this function works in an **inter**-procedural manner and returns all instructions following the current instruction in the CFG (control-flow-graph).

_The function is intra-procedural, and follows function calls; for the **intra**-procedural variant of this function, use_ [_next\_instructions()_](instruction.next_instructions.md)_._



For example, in the function:

```solidity
function approve(address spender, uint256 amount) public override returns (bool) {
        _approve(_msgSender(), spender, amount);
        return true;
    }
```

for the instruction:

```solidity
_approve(_msgSender(), spender, amount);
```

the function will return instructions from `_approve()`.

### Query Example

```python
from glider import *
def query():

  instructions = Functions().with_name("approve").exec(1, 9).instructions().exec(1,1)
  
  return instructions + list(instructions.extended_next_instructions())
```

### Output Example

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
