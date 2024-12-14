---
description: >-
  Returns Contracts object for the contracts from which contract was inherited
  directly or indirectly.
---

# Contract.base\_contracts()

`base_contracts() →` [`Contracts`](../contracts/)

It returns the [Contracts](../contracts/) object representing the base contracts of a Contract. The function is recursive. See the example.

## Example query

```python
from glider import *

def query():
  contracts = Contracts().with_name("Deposit").exec(1)

  result = []

  result.append(contracts[0])

  base_contracts = contracts[0].base_contracts().exec()

  result.extend(base_contracts)
  
  return result
```

## Example output

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

`Deposit` is the main contract. Below this text, a portion of the source code for this contract is provided. You can see that `Deposit` inherits from `Context`, `Ownable`, and `ReentrancyGuard`. The `Context` contract is derived from the `Ownable` contract

### Code Example

```solidity
// SPDX-License-Identifier: MIT
pragma solidity =0.8.19;

...

contract Deposit is Ownable, ReentrancyGuard {
    ...
}
```

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

...

abstract contract Ownable is Context {
    ...
}
```
