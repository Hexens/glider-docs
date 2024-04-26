# Functions.without\_modifier\_names()

`without_modifier_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Functions`](./)

Adds a filter to get functions that don't have any modifier with one of the given names.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions without modifiers from the given list
  functions = Functions().without_modifier_names(['onlyAdmin','onlyOwner']).exec(10)

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
