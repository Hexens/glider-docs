---
description: Returns the canonical name of the variable.
---

# Variable.data

property data: Dict

## Query Example

```python
from glider import *

def query():

  state_variables = (
    StateVariables()
    .exec(5)
  )

  print(state_variables[0].data)

  return state_variables
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (8) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Data example

```json5
{
    '_key': '5e36c16804631f71358ec0d5ed734cb8',
    '_id': 'variables/5e36c16804631f71358ec0d5ed734cb8',
    '_rev': '_iaeY95G--_',
    'name': 'symbol',
    'canonical_name': 'REBITCOIN.symbol',
    'type': {
                'type': 'elementary',
                'name': 'string'
            },
    'visibility': 'public',
    'accessible': True,
    'is_constant': True,
    'is_immutable': False,
    'relative_filepath': 'REBITCOIN.sol',
    'first_source_line': 17,
    'last_source_line': 17,
    'start_column': 5,
    'end_column': 43
}
```
