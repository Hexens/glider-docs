# Functions.with\_modifiers\_name()

Adds a filter to get functions that have a modifier with one of the given names.

Parameters : `names: List[str], sensitivity: bool = True`

```python
from glider import *

def query():
  
  # Fetch a list of functions with modifiers from the given list
  functions = Functions().with_modifiers_name(['onlyAdmin','onlyOwner']).exec(10)

  return functions
```

\


Output:

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "contract": "0x2d8bE62BF76F5c6962E0E44e93374786F329260c",
    "contract_name": "ComposableHolding",
    "sol_function": "function addInvestmentStrategy(address strategyAddress)\n    external\n    onlyAdmin\n    validAddress(strategyAddress)\n    {\n        investmentStrategies[strategyAddress] = true;\n    }"
  },
  {
    "contract": "0x2d8bE62BF76F5c6962E0E44e93374786F329260c",
    "contract_name": "ComposableHolding",
    "sol_function": "function addInvestmentStrategy(address strategyAddress)\n    external\n    onlyAdmin\n    validAddress(strategyAddress)\n    {\n        investmentStrategies[strategyAddress] = true;\n    }"
  }
]
</code></pre>
