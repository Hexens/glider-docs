---
description: Returns a list of delegate call instructions from assembly.
---

# Instructions.delegate\_calls\_from\_assembly()

`delegate_calls_from_assembly() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().delegate_calls_from_assembly().exec(1)
  
  return instructions
```

## Output Example

<pre class="language-solidity"><code class="lang-solidity">{
    "contract": "0x7f57db3bd2616a21a38d9b7b42199450a392ab38"
    "contract_name": "FOG"
    "sol_function":
        function _delegate(address implementation) internal virtual {
                assembly {
                    // Copy msg.data. We take full control of memory in this inline assembly
                    // block because it will not return to Solidity code. We overwrite the
                    // Solidity scratch pad at memory position 0.
                    calldatacopy(0, 0, calldatasize())
         
                    // Call the implementation.
                    // out and outsize are 0 because we don't know the size yet.
                    let result := delegatecall(gas(), implementation, 0, calldatasize(), 0, 0)
         
                    // Copy the returned data.
                    returndatacopy(0, 0, returndatasize())
         
                    switch result
                    // delegatecall returns 0 on error.
                    case 0 {
                        revert(0, returndatasize())
                    }
                    default {
                        return(0, returndatasize())
                    }
                }
            }
<strong>    "sol_instruction":
</strong>        let result := delegatecall(gas(), implementation, 0, calldatasize(), 0, 0)
}
</code></pre>
