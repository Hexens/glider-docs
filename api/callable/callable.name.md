---
description: Returns the function's or modifier's name.
---

# Callable.name()

## Return type

→ str

## Example

```python
from glider import *
def query():
  contracts = Contracts().exec(100)

  contracts_with_callables = []
  for c in contracts:
    contract = {"name": c.name, "functions": [], "modifiers": []}
    # Aggregate the name of all functions for each contract
    for function in c.functions().exec():
      contract["functions"].append(function.name())

    # Same for modifiers
    for modifier in c.modifiers().list():
      contract["modifiers"].append(modifier.name())

    contracts_with_callables.append(contract)

  return contracts_with_callables
```

## Example output

<pre class="language-json"><code class="lang-json"><strong>[
</strong><strong>  {
</strong>    "name": "IERC20",
    "functions": [
      "totalSupply",
      "balanceOf",
      "transfer",
      "allowance",
      "approve",
      "transferFrom"
    ],
    "modifiers": []
  },
  {
    "name": "IERC777",
    "functions": [
      "name",
      "symbol",
      "granularity",
      "totalSupply",
      "balanceOf",
      "send",
      "burn",
      "isOperatorFor",
      "authorizeOperator",
      "revokeOperator",
      "defaultOperators",
      "operatorSend",
      "operatorBurn"
    ],
    "modifiers": []
  },
  ...
]
</code></pre>
