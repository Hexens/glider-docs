---
description: Returns detailed information about the argument variable.
---

# ArgumentVariable.data

## Query Example

```python
from glider import *

def query():

  functions = (
    Functions()
    .exec(1, 50)
    )

  for func in functions:
    args = func.arguments()
    print(args.list()[0].get_variable().data)
  return functions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

### Detailed Output

```json5
{
    'name': 'target',
    'canonical_name': 'Address.functionCallWithValue(address,bytes,uint256,string).target',
    'type': {
        'type': 'elementary',
        'name': 'address'
     }, 
     'memory_type': 'memory'
}
```
