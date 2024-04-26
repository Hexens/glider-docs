# Functions.without\_modifier\_name()

`without_modifier_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Functions`](./)

Adds a filter to get functions that either have no modifier with the given name or have no modifier at all.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions without onlyOwner modifier
  functions = Functions().without_modifier_name('onlyOwner').exec(10)

  return functions
```

## Output

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": "function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }"
  }
]
</code></pre>
