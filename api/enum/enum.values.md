---
description: Returns the values of the enum.
---

# Enum.values

_`property`_` ``value:`` `_`str`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 166)
    i = 0
    contract = contracts[0]
    
    for enum in contract.enums().exec():
      for enum_value in enum.values:
        print(enum_value)

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "NoError",
      "InvalidSignature",
      "InvalidSignatureLength",
      "InvalidSignatureS",
      "InvalidSignatureV"
    ]
  }
]
```
