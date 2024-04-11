# Contract.events()

## Description

The function returns all the events of a Contract.

## Return type

List\[[Event](../event/)]

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(5)
  
  names = []
  for contract in contracts:
    events = contract.events()

    for event in events:
      names.append(event.name)

  return [{"names": names}]
```

## Example output

```json
{
  "names": [
    "OwnershipTransferred",
    "Transfer",
    "Approval",
    "ApprovalForAll"
  ]
}
```
