---
description: Returns the function's properties.
---

# Function.properties()

`properties() → List[`[`MethodProp`](../callables/methodprop/)`]`

Returns the function's properties as a list of [MethodProps](../callables/methodprop/)

## Example

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(1)

  # Retrieve the properties of the first function
  properties = functions[0].properties()
  for prop in properties:
    print(prop)

  return functions
```

## Output

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Context"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
},
"root":{1 item
"print_output":[2 items
0:string"MethodProp.IS_VIEW"
1:string"MethodProp.INTERNAL"
]
}
```
