---
description: Returns the data of the enum.
---

# Enum.data

_`property`_` ``data:`` `_`Dict`_

## Query Example

```python
from glider import *

def query():
    contracts = Contracts().exec(1, 71)

    for enum in contracts[0].enums().exec():
      print(enum.data)

    return []
```

## Example Output

The following query will output the following enum data:

```json
{
    '_key': '1c509fde9e5a2a8dbd30759d4e24e81b', 
    '_id': 'enums/1c509fde9e5a2a8dbd30759d4e24e81b', 
    '_rev': '_jw0UR9m---', 
    'name': 'CollateralManagerErrors', 
    'min': 0, 
    'max': 10, 
    'values': [
        'NO_ERROR', 'NO_COLLATERAL_AVAILABLE', 'COLLATERAL_CANNOT_BE_LIQUIDATED', 
        'CURRRENCY_NOT_BORROWED', 'HEALTH_FACTOR_ABOVE_THRESHOLD', 
        'NOT_ENOUGH_LIQUIDITY', 'NO_ACTIVE_RESERVE', 
        'HEALTH_FACTOR_LOWER_THAN_LIQUIDATION_THRESHOLD', 
        'INVALID_EQUAL_ASSETS_TO_SWAP', 'FROZEN_RESERVE', 'PAUSED_RESERVE'
    ], 
    'relative_filepath': '0xa52E67Ae57E9A029a117145700a2E4514762498C_DefaultReserveInterestRateStrategy.sol', 
    'first_source_line': 565, 
    'last_source_line': 567, 
    'start_column': 3, 
    'end_column': 4, 
    'address': '0xa52E67Ae57E9A029a117145700a2E4514762498C'
}
```
