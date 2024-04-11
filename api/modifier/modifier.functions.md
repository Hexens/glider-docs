# Modifier.functions()

Returns the [Functions](../functions/) object for the functions which have the modifier.

## Return type

→ [Functions](../functions/)

An example to retrieve the functions object for the modifier is as below

```python
from glider import *
def query():
  modifierlist = Modifiers()\
      .name_prefix("check")\
      .exec(5)
  
  results =  []

  for modd in modifierlist:
    for funcs in modd.functions().list():
      results.append(funcs)

  return results
```

## Output
