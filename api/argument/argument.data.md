---
description: Returns the internal data of the Argument
---

# Argument.data

_`property`_` ``data`

It contains the name, canonical\_name, type, and memory\_type of the Argument.

```python
from glider import *


def query():
  functions = Functions().with_arg_count(2).exec(100)
 
  for f in functions:
    for arg in f.arguments().list():
        print(f"Argument: {arg.get_variable().data}")

  return []
```

## Output Example

In the query above, the `data` property will return:

```python
{
    'name': 'recipient', 
    'canonical_name': 'IERC20.transfer(address,uint256).recipient', 
    'type': {
        'type': 'elementary', 
        'name': 'address'
    }, 
    'memory_type': 'memory'
}
```
