# Contract.errors()

## Description

The function returns all the errors of a Contract.

## Return type

List\[Error]

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(5, 150)
  
  names = []
  for contract in contracts:
    errors = contract.errors()

    for error in errors:
      names.append(error.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "InvalidArgument",
    "FailedToSendEther"
  ]
}
```
