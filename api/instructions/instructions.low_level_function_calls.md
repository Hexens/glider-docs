---
description: Returns a list of the functions calls instructions
---

# Instructions.low\_level\_function\_calls()

`low_level_function_calls() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().low_level_function_calls().exec(1)

  return instructions
```

## Output Example

<pre class="language-solidity"><code class="lang-solidity">{
<strong>    "contract": "0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
</strong>    "contract_name": "Address"
    "sol_function":
        function sendValue(address payable recipient, uint256 amount) internal {
            require(address(this).balance >= amount, "Address: insufficient balance");
    
            (bool success, ) = recipient.call{value: amount}("");
            require(success, "Address: unable to send value, recipient may have reverted");
        }
    "sol_instruction":
        (bool success, ) = recipient.call{value: amount}("")
}
</code></pre>

## Note

TBD: rename to `low_level_external_calls()`
