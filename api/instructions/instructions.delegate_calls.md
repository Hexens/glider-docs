---
description: Returns a list of all delegate call instructions.
---

# Instructions.delegate\_calls()

**`delegate_calls`**`() →` [`Instructions`](./)

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

<pre class="language-solidity"><code class="lang-solidity">{
    "contract":"0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
    "contract_name":"Address"
<strong>    "sol_function":
</strong>        function functionDelegateCall(
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
</code></pre>
