# Instructions.modifiers()

**`modifiers`**`() →` [`Modifiers`](../modifiers/)

Returns [Modifiers](../modifiers/) object for the modifiers of the instructions. Note: The function will return parent modifiers for those instructions that belong to a modifier, not to a function. To get parent functions of that instructions use `functions()` method.

## Return type

`→` [`Modifiers`](../modifiers/)

## Query Example

```python
from glider import *

def query():
  # Fetch a list of modifiers of the instructions
  instructions = Instructions().modifiers().exec(1)

  return instructions
```

## Output Example

<pre class="language-solidity"><code class="lang-solidity">{
<strong>    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
</strong>    "contract_name": "Ownable"
    "sol_modifier": 
        modifier onlyOwner() {
            require(_owner == _msgSender(), "Ownable: caller is not the owner");
            _;
        }
}
</code></pre>
