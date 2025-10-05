# Modifier.placeholder\_instructions()

`placeholder_instructions() →` [`Instructions`](../instructions/)

Returns placeholder [instructions](../instruction/) of the [modifier](../callable/modifier/).

The placeholder or placer instruction is the "\_" (underline) instruction which defines where the function code must be inline in the modifier.

## Return type

→ List\[[Instruction](../instruction/)]

An example of a query which can analyze placeholder instructions is:

```python
from glider import *

def query():
  modifierlist = (
      Modifiers()
      .with_name_prefix("lock")
      .exec(3)
  )
  
  results =  []

  for modd in modifierlist:
    for placers in modd.placeholder_instructions().exec():
      results.append(placers)

  return results
```

## Output

<figure><img src="../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>
