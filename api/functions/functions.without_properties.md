# Functions.without\_properties()

Adds a filter to get functions that don't have any of the given properties.

Parameters : `properties: List[MethodProp]`

```python
from glider import *

def query():
  
  # Fetch a list of functions which are not external/public
  functions = Functions().without_properties([MethodProp.EXTERNAL, MethodProp.PUBLIC]).exec(10)

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
