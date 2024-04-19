---
description: Returns the index of the argument.
---

# Argument.index

_`property`_` ``index`_`: int`_



```python
from glider import *
def query():
  functions = Functions().with_arg_count(5).exec(1)

  function_with_args = []
  for f in functions:
    # For each of its arguments...
    for arg in f.arguments().list():
        # ...return the data of the argument
        print(arg.source_code()+'\n\n'+str(arg.index))

  return functions
```

## Output

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"IUniswapV2Router02"
"sol_function":solidity
function swapExactTokensForETHSupportingFeeOnTransferTokens(
        uint amountIn,
        uint amountOutMin,
        address[] calldata path,
        address to,
        uint deadline
    ) external;
},
"root":{1 item
        "print_output":[5 items
        0:string"uint256 amountIn
        
        0"
        1:string"uint256 amountOutMin
        
        1"
        2:string"address[] path
        
        2"
        3:string"address to
        
        3"
        4:string"uint256 deadline
        
        4"
        ]
}
```
