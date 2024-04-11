---
description: Returns a serialized JSON representation of the function/modifier.
---

# Callable.dump\_into\_json()

## Return type

→ Dict

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  json = []
  for function in functions:
    # Get serialized informations about each function
    json.append(function.dump_into_json())

  return json
```

## Example output

```json
[
  {
    "_key": "96e8caf747cd59ead8760cead194a8d0",
    "_id": "functions/96e8caf747cd59ead8760cead194a8d0",
    "_rev": "_h_ZmbDi---",
    "name": "_msgSender",
    "relative_filepath": "../smart-contract-sanctuary-ethereum/contracts/kovan/79/798AcB51D8FBc97328835eE2027047a8B54533AD_LTP.sol",
    "signature": "_msgSender()",
    "hashed_signature": 295563871,
    "is_override": false,
    "first_source_line": 19,
    "last_source_line": 21,
    "start_column": 5,
    "end_column": 6,
    "declarer_contract_name": "Context",
    "callees": {
      "internal": [],
      "high_level": [],
      "library_calls": [],
      "low_level": [],
      "solidity": []
    },
    "args": [],
    "local_vars": [],
    "state_variables_read": [],
    "state_variables_written": [],
    "modifiers": [],
    "is_constructor": false,
    "is_payable": false,
    "is_pure": false,
    "is_view": true,
    "visibility": "internal",
    "edges": [[0, 1]],
    "errors": [],
    "return": [["address", ""]],
    "is_global": false
  },
  ...
]
```
