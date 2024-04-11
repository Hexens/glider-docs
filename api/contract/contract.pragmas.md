# Contract.pragmas()

## Description

Returns the list of all pragmas of the contract.

## Return type

List\[Tuple\[str, str]]

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1, 100)
  
  result = []
  for contract in contracts:
    pragmas = contract.pragmas()
    result.append(pragmas[0])

  return result
```

## Example output

```json
[
  "../smart-contract-sanctuary-ethereum/contracts/kovan/40/400a7e0960b63d3288591ee0e6B6D9578eAFFe23_ChainlinkInceptionPriceFeed.sol",
  [
    [
      "experimental",
      "ABIEncoderV2"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      ">=",
      "0.6",
      ".0",
      "<",
      "0.8",
      ".0"
    ],
    [
      "solidity",
      ">=",
      "0.6",
      ".0",
      "<",
      "0.8",
      ".0"
    ],
    [
      "solidity",
      ">=",
      "0.4",
      ".24",
      "<",
      "0.8",
      ".0"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      ">=",
      "0.6",
      ".0",
      "<",
      "0.8",
      ".0"
    ],
    [
      "solidity",
      ">=",
      "0.6",
      ".0",
      "<",
      "0.8",
      ".0"
    ],
    [
      "solidity",
      ">=",
      "0.6",
      ".2",
      "<",
      "0.8",
      ".0"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ],
    [
      "solidity",
      "0.6",
      ".12"
    ]
  ]
]
```
