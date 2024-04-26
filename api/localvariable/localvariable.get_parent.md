---
description: Returns parent function/modifier of the local variable.
---

# LocalVariable.get\_parent()

`get_parent() →` [`Callable`](../callable/)

The function returns the [Function](../callable/function/) or [Modifier](../callable/modifier/) object of the function/modifier where the local variable is declared.

**Query Example**

```python
from glider import *
def query():
  funcs = Functions().exec(500)

  for func in funcs:
    local_vars = func.local_variables().list()
    for local_var in local_vars:
      print(local_var.name)
      print(local_var.memory_type)
      return [local_var.get_parent()]

  return []
```

**Output**

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function add(uint256 a, uint256 b) internal pure returns (uint256) {
        uint256 c = a + b;
        require(c >= a, "SafeMath: addition overflow");
        return c;
    }
},
"root":{1 item
"print_output":[2 items
0:string"c"
1:string"default"
]
}
```
