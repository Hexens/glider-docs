# Modifiers.placeholder\_instructions()

`placeholder_instructions() →` [`Instructions`](../instructions/)

Returns placeholder [instructions](../instructions/) for the set of [Modifiers](../callables/modifiers/).

The placeholder or placer instruction is the "\_" (underline) instruction which defines where the function code must be inline in the modifier.

## Query Example

An example to retrieve the instructions used by the modifiers with the name `lock` is as below

```python
from glider import *
def query():
  instructionlist = Modifiers()\
      .with_name("lock")\
      .placer_instructions()\
      .exec(5,5)
  return instructionlist
```

## Example Output

<figure><img src="../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>
