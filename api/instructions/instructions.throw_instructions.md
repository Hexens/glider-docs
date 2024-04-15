# Instructions.throw\_instructions()

Returns an [Instructions](./) object for the 'throw' instructions

`throw_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().throw_instructions().exec(1)

  return instructions
```

## Output Example

<pre class="language-solidity"><code class="lang-solidity">{
    "contract":"0x6c4c4759659d644cb36df4842a7f113321e3f7bb"
    "contract_name":"SafeMath"
<strong>    "sol_function":
</strong>        function assert(bool assertion) internal {
            if (!assertion) throw;
        }
    "sol_instruction":
        throw
}
</code></pre>
