---
description: Returns an Arguments object for the arguments of the function/modifier.
---

# Callable.arguments()

`arguments() → ArgumentPoints`

## Example

```python
from glider import *

def query():
    functions = Functions().exec(1,4)

    for func in functions:
        for arg in func.arguments().list():
            print(f"Function name: {func.name}, Argument: {arg.source_code()}")

    return functions

```

## Example output

```solidity
[
  {
    "contract": "0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "contract_name": "REBITCOIN",
    "contract_link": "https://etherscan.io/address/0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
    "uuid": "9d43cae9-de12-4774-9d46-689b90409b7c",
    "severity": "",
    "sol_function": 
      function transfer(address _to, uint256 _amount) returns (bool success) 
       {
          ...
       }
  },
  {
    "print_output": [
      "Function name: transfer, Argument: address _to",
      "Function name: transfer, Argument: uint256 _amount"
    ]
  }
]
```



{% hint style="info" %}
The function returns ArgumentPoints, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
