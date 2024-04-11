# Instructions.delegate\_calls()

**`delegate_calls`**`() →` [`Instructions`](./)

Returns a list of all delegate call instructions.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a lis of delegatecall instructions
  instructions = Instructions().delegate_calls().exec(1)
  
  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Address",
  "sol_function": "function functionDelegateCall(
        address target,bytes memory data,string memory errorMessage
    ) internal returns (bytes memory) {
        require(isContract(target),"Address: delegate call to non-contract");

        (bool success,bytes memory returndata) = target.delegatecall(data);
        return verifyCallResult(success,returndata,errorMessage);
    }",
  "sol_instruction": "(bool success,bytes memory returndata) = target.delegatecall(data)"
}
```
