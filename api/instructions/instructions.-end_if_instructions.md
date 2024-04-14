---
description: Returns an Instructions object for the 'end if' instructions.
---

# Instructions. end\_if\_instructions()

## Function Signature

`end_if_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().end_if_instructions().exec(1)
  
  return instructions
```

## Output Example

<pre class="language-solidity"><code class="lang-solidity">{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
<strong>    "contract_name": "SafeMath"
</strong>    "sol_function":
        function mul(uint256 a, uint256 b) internal pure returns (uint256) {
                if (a == 0) {
                    return 0;
                }
                uint256 c = a * b;
                require(c / a == b, "SafeMath: multiplication overflow");
                return c;
            }
<strong>    "sol_instruction":
</strong>        if (a == 0) {
                    return 0;
                }
}
</code></pre>
