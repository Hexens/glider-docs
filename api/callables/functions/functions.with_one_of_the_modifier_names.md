# Functions.with\_one\_of\_the\_modifier\_names()

`with_one_of_the_modifier_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Functions`](./)

Adds a filter to get functions that have a modifier with one of the given names.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions with modifiers from the given list
  functions = Functions().with_one_of_the_modifier_names(['onlyAdmin','onlyOwner']).exec(10)

  return functions
```

## Output

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
