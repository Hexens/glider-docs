---
description: Returns the Instruction's Value object.
---

# Instruction.get\_value()

`get_value() ->` [`Value`](../value/) `|` [`NoneObject`](../internal/noneobject/)

## Query Example

```python
from glider import *

def query():
    instructions = Instructions().exec(5)
    results = []
    
    for inst in instructions: 
        print(inst.get_value())

    return instructions
```

## Example Output

```solidity
[
  {
    "contract": "0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "contract_name": "REBITCOIN",
    "contract_link": "https://etherscan.io/address/0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "uuid": "3504dbc6-96ce-434a-ba41-6bbe6586e7bd",
    "severity": "",
    "sol_function": 
      function REBITCOIN()
        //this is the token contract name, change to liking//
  
        {
           owner = msg.sender;
           balances[owner] = _totalSupply;
        }
    "sol_instruction": 
      {
        owner = msg.sender;
        balances[owner] = _totalSupply;
      }
  },
  {
    "contract": "0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "contract_name": "REBITCOIN",
    "contract_link": "https://etherscan.io/address/0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "uuid": "74d783b0-22fb-425c-9c38-d2fb5f020d14",
    "severity": "",
    "sol_function": 
      function REBITCOIN()
        //this is the token contract name, change to liking//
  
        {
           owner = msg.sender;
           balances[owner] = _totalSupply;
        }
    "sol_instruction": 
      owner = msg.sender
  },
  {
    "contract": "0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "contract_name": "REBITCOIN",
    "contract_link": "https://etherscan.io/address/0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "uuid": "476ce4ab-819f-4e48-9f65-8a13ce3da53e",
    "severity": "",
    "sol_function": 
      function REBITCOIN()
        //this is the token contract name, change to liking//
  
        {
           owner = msg.sender;
           balances[owner] = _totalSupply;
        }
    "sol_instruction": 
      balances[owner] = _totalSupply
  },
  {
    "print_output": [
      <api.none_object.NoneObject object at 0x7f2d31fe6a10>,
      <api.value.ValueExpression object at 0x7f2d31e36910>,
      <api.value.ValueExpression object at 0x7f2d31ff8950>
    ]
  }
]
```
