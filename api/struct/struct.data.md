---
description: Returns the data of the struct.
---

# Struct.data

_`property`_` ``data :`` `_`Dict`_

## Query Example

```python
from glider import *


def query():
  contracts = Contracts().with_name("DefaultReserveInterestRateStrategy").exec(1)

  for contract in contracts:
    for struct in contract.structs().exec():
      print(struct.data)

  return contracts
```

## Example Output

Input below represents the return value of struct.data:

```python
{
    '_key': 'd579420667d21aefc3e8d360573a0b7f', 
    '_id': 'structs/d579420667d21aefc3e8d360573a0b7f', 
    '_rev': '_jw0UR9a-_M', 
    'name': 'CalcInterestRatesLocalVars', 
    'fields': [
        {
            'name': 'totalDebt', 
            'type': 
                {
                    'type': 'elementary', 
                    'name': 'uint256'
                }
            }, 
            {
                'name': 'currentVariableBorrowRate', 
                'type': {
                    'type': 'elementary', 
                    'name': 'uint256'
                }
            }, {
                'name': 'currentStableBorrowRate', 
                'type': {
                    'type': 'elementary', 
                    'name': 'uint256'
                }
            }, {
                'name': 'currentLiquidityRate', 
                'type': {
                    'type': 'elementary', 
                    'name': 'uint256'
                }
            }, {
                'name': 'utilizationRate', 
                'type': {
                    'type': 'elementary', 
                    'name': 'uint256'
                }
            }
        ], 
        'relative_filepath': '0xa52E67Ae57E9A029a117145700a2E4514762498C_DefaultReserveInterestRateStrategy.sol', 
        'first_source_line': 148, 
        'last_source_line': 154, 
        'start_column': 3, 
        'end_column': 4, 
        'address': '0xa52E67Ae57E9A029a117145700a2E4514762498C'
    }
}
```
