---
description: Returns the instructions which are reachable from the entry node
---

# Callable.get\_reachable\_instructions()

`get_reachable_instructions() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](../instruction/)`]`

## Query Example

```python
from glider import *

def query():
    functions = Functions().exec(1) 
  
    for reachable_instruction in list(functions[0].get_reachable_instructions()):
        print(f"{reachable_instruction.source_code()}")

    return functions
```

## Example Output

```solidity
[
  {
    "contract": "0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "contract_name": "REBITCOIN",
    "contract_link": "https://etherscan.io/address/0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "uuid": "8b849e25-e396-40c6-ad06-3933aacc7be1",
    "severity": "",
    "sol_function": 
      function REBITCOIN()
         //this is the token contract name, change to liking//
    
         {
            owner = msg.sender;
            balances[owner] = _totalSupply;
         }
      },
  {
    "print_output": [
      {
          owner = msg.sender;
          balances[owner] = _totalSupply;
      },   
      owner = msg.sender,
      balances[owner] = _totalSupply
    ]
  }
]
```
