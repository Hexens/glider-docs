---
description: Returns true if the function is constructor, otherwise returns false.
---

# Function.is\_constructor()

`is_constructor() → bool`

## Example

```python
from glider import *

def query():
  functions = Functions().with_name('constructor').exec(1)
  for function in functions:
    print(function.is_constructor())

  return functions
```

## Output

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Ownable"
"sol_function":solidity
constructor () {
        address msgSender = _msgSender();
        _owner = msgSender;
        emit OwnershipTransferred(address(0), msgSender);
    }
},
"root":{1 item
"print_output":[1 item
0:string"True"
]
}
```
