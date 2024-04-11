# Functions.constructors()

Adds a filter to get only the constructors.

```python
from glider import *

def query():
  # Fetch a list of constructors
  functions = Functions().constructors().exec(2)

  return functions
```

\


Output:

<pre class="language-json"><code class="lang-json"><strong>[
</strong><strong>  {
</strong>    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "constructor() {\n        _setOwner(_msgSender());\n    }"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "ERC721",
    "sol_function": "constructor(string memory name_,string memory symbol_) {\n        _name = name_;\n        _symbol = symbol_;\n    }"
  }
]
</code></pre>
