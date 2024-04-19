---
description: Returns the list of local variables having specified type.
---

# LocalVariables.with\_type()

`with_type(var_type: str) → List[`[`LocalVariable`](../localvariable/)`]`

**Query Example**

```python
from glider import *
def query():
  funcs = Functions().exec(1000)

  for func in funcs:
    local_vars = func.local_variables().with_type('bytes')
    for local_var in local_vars:
      print(local_var.name)
      print(local_var.type.name)
      return [local_var.get_parent()]

  return []
```

**Output**

```solidity
"root":{3 items
"contract":string"0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
"contract_name":string"Strings"
"sol_function":solidity
function toHexString(uint256 value, uint256 length) internal pure returns (string memory) {
        bytes memory buffer = new bytes(2 * length + 2);
        buffer[0] = "0";
        buffer[1] = "x";
        for (uint256 i = 2 * length + 1; i > 1; --i) {
            buffer[i] = _SYMBOLS[value & 0xf];
            value >>= 4;
        }
        require(value == 0, "Strings: hex length insufficient");
        return string(buffer);
    }
}
"root":{1 item
"print_output":[2 items
0:string"buffer"
1:string"bytes"
]
}
```
