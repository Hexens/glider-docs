---
description: Returns the list of all structs of the contract.
---

# Contract.structs()

`structs() → List[Struct]`

## Example query

```python
from glider import *

def query():
    contracts = Contracts().exec(50)

    for contract in contracts:
        for struct in contract.structs().exec():
            print(struct.name)
        
    return contracts
```

## Example output

```json
[
  ...
  {
    "print_output": [
      "TokenOwnership",
      "AddressData",
      "AddressSlot",
      "BooleanSlot",
      "Bytes32Slot",
      "Uint256Slot",
      "Slot0",
      "ProtocolFees",
      "ModifyPositionParams",
      "SwapCache",
      "SwapState",
      "StepComputations"
    ]
  }
]
```
