# Instructions. return\_instructions()

Returns an [Instructions](./) object for the 'return' instructions.

`return_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().return_instructions().exec(1)

  return instructions
```

## Output Example

<pre class="language-solidity"><code class="lang-solidity">{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
<strong>    "contract_name": "Context"
</strong>    "sol_function":
        function _msgSender() internal view virtual returns (address) {
            return msg.sender;
        }
    "sol_instruction":
        return msg.sender
}
</code></pre>
