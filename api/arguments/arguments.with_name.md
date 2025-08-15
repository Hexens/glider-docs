---
description: Returns a list of arguments having specified name
---

# Arguments.with\_name()

`with_name(arg_name: str, sensitivity: bool = False) -> List[`[`Argument`](../argument/)`]`

## Query Example

```python
from glider import *
 

def query():
  functions = Functions().exec(1000)

  for f in functions:
    # Find arguments named "account"
    for arg in f.arguments().with_name("account"):
      print(arg.get_variable().data)

  return []
```

## Output Example&#x20;

Example output of an Argument named "account":

```json
{
    'name': 'account', 
    'canonical_name': 'Datagold.queryAccountInfo(address,string).account', 
    'type': {
        'type': 'elementary', 
        'name': 'address'
    }, 
    'memory_type': 'memory'
}
```
