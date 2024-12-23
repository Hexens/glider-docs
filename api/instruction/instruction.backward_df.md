---
description: >-
  Returns a list of all previous instructions/arguments/variables of the current
  point in the data flow graph.
---

# Instruction.backward\_df()

`backward_df() →` [`APISet`](../iterables/apiset.md)`[`[`Point`](../point/)`]`

The `backward_df()` function is an intra-procedural analysis function. This means that the function does not operate recursively and instead returns `instruction/argument/variable` within the current function instruction set.

The function returns the derived classes from [Point](../point/), such as [ArgumentPoint](../point/argumentpoint.md), [VarValue](../point/varvalue/), [Instruction](./), etc.

## Query Example

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().with_callee_function_name('verify').exec(1)
  
  for points in instructions[0].backward_df():
    print(points.source_code())
  # return the list of previous instructions of the current instruction
  return instructions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (180).png" alt=""><figcaption></figcaption></figure>

For the same contract, this query showcases that the return list elements are type-casted from Point:

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().with_callee_function_name('verify').exec(1)
  
  for points in instructions[0].backward_df():
    if isinstance(points, ArgumentPoint):
      print(points.get_variable().name)
    print(points.source_code())
  # return the list of previous instructions of the current instruction
  return instructions
```

<figure><img src="../../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>



{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
