---
description: Returns the function's/modifier's instructions that create a new contract.
---

# Callable.new\_contract\_instructions()

`new_contract_instructions() →` [`Instructions`](../instructions/)

## Query Example

```python
from glider import *

def query():
  functions = Functions().with_name("deploy").exec(20)

  deployment_instructions = []
  for func in functions:
    for inst in func.new_contract_instructions().exec():
      deployment_instructions.append(inst)
      
  return deployment_instructions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>
