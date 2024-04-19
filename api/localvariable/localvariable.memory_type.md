---
description: Returns the memory type of the local variable.
---

# LocalVariable.memory\_type

`property name: str`

The memory type can be `calldata, memory, storage, default (stack)`

**Query Example**

```python
from glider import *
def query():
  funcs = Functions().exec(500)

  for func in funcs:
    local_vars = func.local_variables().list()
    for local_var in local_vars:
      if local_var.memory_type == 'memory':
        print(local_var.name)
        print(local_var.memory_type)
        return [local_var.get_parent()]

  return []
```

**Output**

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Token"
"sol_function":solidity
function swapTokensForEth(uint256 tokenAmount) private lockTheSwap {
        address[] memory path = new address[](2);
        path[0] = address(this);
        path[1] = uniswapV2Router.WETH();
        uniswapV2Router.swapExactTokensForETHSupportingFeeOnTransferTokens(
            tokenAmount,
            0,
            path,
            address(this),
            block.timestamp
        );
    }
},
"root":{1 item
"print_output":[2 items
0:string"path"
1:string"memory"
]
}
```
