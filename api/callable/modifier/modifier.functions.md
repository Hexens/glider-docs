# Modifier.functions()

`functions() →` [`Functions`](../../callables/functions/)

Returns the [Functions](../../callables/functions/) object for the functions which have the modifier.



An example to retrieve the functions object for the modifier is as below

```python
from glider import *
def query():
  modifierlist = Modifiers()\
      .with_name_prefix("check")\
      .exec(1)
  
  results =  []

  for modd in modifierlist:
    for funcs in modd.functions().exec():
      results.append(funcs)

  return results
```

## Output

<figure><img src="../../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

