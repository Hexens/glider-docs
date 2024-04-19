---
description: Returns true if the Contract is main, false otherwise.
---

# Contract.is\_main()

`is_main() → bool`

The engine marks the contract as main, if it is the one being executed on the deployed address

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(10, 10)
  
  mains = []
  for contract in contracts:
    if contract.is_main():
      mains.append(contract)

  return mains
```

## Example output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "LTP"
}
```
