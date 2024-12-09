---
description: Returns the function's/modifier's instructions that create a new contract.
---

# Callable.new\_contract\_instructions()

`new_contract_instructions() →` [`Instructions`](../instructions/)

## Query Example

```python
from glider import *

def query():
  functions = Functions().with_name("deploy").exec(100)

  deployment_instructions = []
  for func in functions:
    for inst in func.new_contract_instructions().exec():
      deployment_instructions.append(inst)
      
  return deployment_instructions
```

## Output Example

```solidity
[
  {
    "contract": "0xede551885bc51c46bb0da6ad0b6268396eb8aebf",
    "contract_name": "BorrowerDeployer",
    "contract_link": "https://etherscan.io/address/0xede551885bc51c46bb0da6ad0b6268396eb8aebf",
    "uuid": "799ab116-c846-452f-b1e9-0c5690297bc0",
    "severity": "",
    "sol_function": 
      function deploy(
        VolatilityOracle oracle,
        IUniswapV3Pool pool,
        Lender lender0,
        Lender lender1
      ) external returns (Borrower) {
        return new Borrower(oracle, pool, lender0, lender1);
      },
    "sol_instruction": "return new Borrower(oracle, pool, lender0, lender1)"
  },
  ...
]
```
