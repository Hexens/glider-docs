# Functions.with\_modifier\_name\_not()

Adds a filter to get functions that either have no modifier with the given name or have no modifier at all.

Parameters : `name: str, sensitivity: bool = True`

```python
from glider import *

def query():
  
  # Fetch a list of functions without onlyOwner modifier
  functions = Functions().with_modifier_name_not('onlyOwner').exec(10)

  return functions
```

\


Output:

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
