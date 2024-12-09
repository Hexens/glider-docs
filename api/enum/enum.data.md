---
description: Returns the data of the enum.
---

# Enum.data

_`property`_` ``data:`` `_`Dict`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 166)
    i = 0
    contract = contracts[0]
    
    for enum in contract.enums().exec():
      print(enum.data)

    return []
```

## Example Output

```json
[
  {
    "print_output": [
      "{
        '_key': '909658d784f7d811f4be3298f29f043a', 
        '_id': 'enums/909658d784f7d811f4be3298f29f043a', 
        '_rev': '_iaelzA----', 
        'name': 'RecoverError', 
        'relative_filepath': '0x96f19828529bFEf13e6aC64DE952cedA2d866f2f_RainVestingV2.sol', 
        'min': 0, 
        'max': 4, 
        'values': [
          'NoError', 
          'InvalidSignature', 
          'InvalidSignatureLength', 
          'InvalidSignatureS', 
          'InvalidSignatureV'
        ]
      }"
    ]
  }
]
```
