---
description: >-
  Returns a Functions object representing the functions through which the
  functions from current Functions object could be called.
---

# Functions.extended\_caller\_functions()

`extended_caller_functions() →` [`Functions`](../callables/functions/)

The function will retrieve _**extended**_**/**_**inter-procedural**_ functions, meaning it works recursively. It returns the Functions object representing all the functions that ultimately call the function in question.

## Query Example

```python
from glider import *

def query():
  funcs = Functions().with_name("withdrawFromPair").extended_caller_functions().exec(2)
  
  return funcs
```

## Output Example

```solidity
{
  "content": [
    {
      "contract": "0x0ed8fa7fc63a8eb5487e7f87caf1ab3914ea4eca",
      "contract_name": "FraxlendAMO",
      "sol_function": solidity
        function withdrawMaxFromPair(address _pairAddress) public onlyByOwnerOperator returns (uint256 _amountWithdrawn) {
            IFraxlendPair _fraxlendPair = IFraxlendPair(_pairAddress);
            uint256 _shares = _fraxlendPair.balanceOf(address(this));
            if (_shares == 0) {
                return 0;
            }
            _fraxlendPair.addInterest();
            (uint128 _totalAssetAmount, ) = _fraxlendPair.totalAsset();
            (uint128 _totalBorrowAmount, ) = _fraxlendPair.totalBorrow();  
            uint256 _availableAmount = _totalAssetAmount - _totalBorrowAmount;
            uint256 _availableShares = _fraxlendPair.toAssetShares(_availableAmount,false);
            if (_shares <= _availableShares) {
                _amountWithdrawn = withdrawFromPair(_pairAddress, _shares);
            } else {
                _amountWithdrawn = withdrawFromPair(_pairAddress, _availableShares);
            }
        }
      "sol_function_source_lines": [
        416,
        432
      ]
    },
    {
      "contract": "0x0ed8fa7fc63a8eb5487e7f87caf1ab3914ea4eca",
      "contract_name": "FraxlendAMO",
      "sol_function":solidity
          function withdrawMaxFromAllPairs() public onlyByOwnerOperator {
              address[] memory _pairsArray = pairsArray;
              for (uint256 i = 0; i < _pairsArray.length; i++) {
                  withdrawMaxFromPair(_pairsArray[i]);
              }
          }
      "sol_function_source_lines": [
        435,
        440
      ]
    }
  ]
}
```
