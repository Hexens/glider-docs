---
description: Returns a list of delegate call instructions from non assembly.
---

# Instructions.delegate\_calls\_non\_assembly()

`delegate_calls_non_assembly() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().delegate_calls_non_assembly().exec(1)
  
  return instructions
```

## Output Example

```solidity
{
    "contract": "0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
    "contract_name": "Address"
    "sol_function":
        function functionDelegateCall(
                address target,
                bytes memory data,
                string memory errorMessage
            ) internal returns (bytes memory) {
                (bool success, bytes memory returndata) = target.delegatecall(data);
                return verifyCallResultFromTarget(target, success, returndata, errorMessage);
            }
    "sol_instruction":
        (bool success, bytes memory returndata) = target.delegatecall(data)

}
```
