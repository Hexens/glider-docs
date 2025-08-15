---
description: Returns a list of arguments having specified memory type.
---

# Arguments.with\_memory\_type()

`with_memory_type(memory_type: str) -> List[`[`Argument`](../argument/)`]`

## Query Example

```python
from glider import *


def query():
  functions = Functions().exec(1000)

  for f in functions:
    # Find arguments that have storage memory types
    for arg in f.arguments().with_memory_type("storage"):
      print(arg.get_variable().data)

  return []
```

## Output Example

Example output of a memory storage Argument:

```python
{
    'name': 'role', 
    'canonical_name': 'Roles.add(Roles.Role,address).role', 
    'type': {
        'type': 'struct', 
        'name': 'Role', 
        'contract_name': 'Roles', 
        'relative_filepath': '0xa5CFFF6a2c1a48AE38e8279Cf708AdbF16023e50_Exercies.sol'
    }, 
    'memory_type': 'storage'
}
```
