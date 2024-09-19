---
description: >-
  with_one_property is deprecated and will be removed in future versions. Please
  use with_properties in- stead. Adds a filter to get functions that at least
  have one of the given properties.
---

# Functions.with\_one\_property()

**Deprecated:** This method is deprecated and will be removed in future versions.

**Alternative:** Use `with_properties()` instead for improved functionality.

`with_one_property(`_`properties: List[MethodProp]`_`) →` [`Functions`](./)

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions which a external
  functions = Functions().with_one_property([MethodProp.EXTERNAL]).exec(10)

  return functions
```

## Output

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "IERC165",
    "sol_function": "function supportsInterface(bytes4 interfaceId) external view returns (bool);"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "IERC721",
    "sol_function": "function supportsInterface(bytes4 interfaceId) external view returns (bool);"
  }
]
</code></pre>
