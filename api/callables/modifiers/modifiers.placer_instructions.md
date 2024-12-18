# Modifiers.placer\_instructions()

`placer_instructions() →` [`Instructions`](../../instructions/)

Returns placeholder [instructions](../../instructions/) for the set of [Modifiers](./).

The placeholder or placer instruction is the "\_" (underline) instruction which defines where the function code must be inline in the modifier.

## Return type

→ [Instructions](../../instructions/)

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

## Output

<figure><img src="../../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>
