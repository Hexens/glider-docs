# Instructions.static\_calls()

**`static_calls`**`() →` [`Instructions`](./)

Returns a list of all static call instructions.

Only solidity's low level `staticcall()` is returned.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of low level static calls instructions
  instructions = Instructions().static_calls().exec(10)

  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Address",
  "sol_function": function functionStaticCall(
        address target,bytes memory data,string memory errorMessage
    ) internal view returns (bytes memory) {
        require(isContract(target),"Address: static call to non-contract");

        (bool success,bytes memory returndata) = target.staticcall(data);
        return verifyCallResult(success,returndata,errorMessage);
    },
  "sol_instruction": (bool success,bytes memory returndata) = target.staticcall(data)
}
```
