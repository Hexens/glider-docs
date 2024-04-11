# Contract.is\_lib()

## Description

Returns true if the Contract is a library, false otherwise.

## Return type

bool

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(25)
  
  libs = []
  for contract in contracts:
    if contract.is_lib():
      libs.append(contract)

  return libs
```

## Example output

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Address"
}
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Strings"
}
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "SuperAppDefinitions"
}
```
