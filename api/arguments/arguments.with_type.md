---
description: Returns a list of arguments having specified memory type.
---

# Arguments.with\_type()

`with_type(`_`arg_type: str`_`) → List[`[`Argument`](../argument/)`]`

## Query Example

```python
from glider import *
 
 
def query():
  functions = Functions().exec(1000)

  for f in functions:
    # Find arguments that are the bytes32 type 
    for arg in f.arguments().with_type("bytes32"):
      print(arg.get_variable().data)

  return []
```

## Output Example

Example output of an Argument with the memory type bytes32:

```json
{
    'name': '_keyHash', 
    'canonical_name': 'VRFRequestIDBase.makeVRFInputSeed(bytes32,uint256,address,uint256)._keyHash', 
    'type': {
        'type': 'elementary', 
        'name': 'bytes32'
    }, 
    'memory_type': 'memory'
}
```
