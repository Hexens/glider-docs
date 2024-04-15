---
description: Returns a list of all low level static call instructions.
---

# Instructions.low\_level\_static\_calls()

`low_level_static_calls() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().low_level_function_calls().exec(1)

  return instructions
```

## Output Example

```solidity
{
    "contract": "0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
    "contract_name": "Address"
    "sol_function":
    function functionStaticCall(
            address target,
            bytes memory data,
            string memory errorMessage
        ) internal view returns (bytes memory) {
            (bool success, bytes memory returndata) = target.staticcall(data);
            return verifyCallResultFromTarget(target, success, returndata, errorMessage);
    }
    "sol_instruction":
        (bool success, bytes memory returndata) = target.staticcall(data)
}
```
