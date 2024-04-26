---
description: >-
  Returns a Functions object that represents called functions from the
  function/modifier.
---

# Callable.callee\_functions()

`callee_functions() →` [`Functions`](../functions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  called_functions = []
  for function in functions:
    for called in function.callee_functions().exec():
      # Return each called function from this specific one
      called_functions.append(called)

  return called_functions
```

## Example output

```solidity
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    // Formatted for the example
    "sol_function": `
    function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
    `
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    // Formatted for the example
    "sol_function": `
    function _setOwner(address newOwner) private {
        address oldOwner = _owner;
        _owner = newOwner;
        emit OwnershipTransferred(oldOwner,newOwner);
    }
    `
  },
  ...
]
```
