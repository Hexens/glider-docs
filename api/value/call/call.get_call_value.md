---
description: >-
  Returns the Value representing the "value" (ether sent) during the external
  call
---

# Call.get\_call\_value()

`get_call_value() → List[`[`Value`](../)`]`

As some types of calls can have, a special parameter set representing the ether value to send in the call), this function can be used to retrieve that value.

For example, in the call:

```solidity
uniswapV2Router.addLiquidityETH{value: address(this).balance}(address(this),balanceOf(address(this)),0,0,owner(),block.timestamp)
```

The special parameter `value` is being set: `{value: address(this).balance}`

and the function will return the Value representing the:

`address(this).balance`

**Query Example**

```python
from glider import *

def query():
  instructions = Instructions().external_calls().exec(30)

  results = []
  for instruction in instructions:
    for call in instruction.get_callee_values():
        for value in call.get_call_value():
          print(value.expression, value)
          results.append(instruction)

  return results
```

**Output**

```solidity
"root":{4 items
"contract":string"0xe2664f5a19b5138f866b7bdb3d14119bca999de2"
"contract_name":string"GrandPaPEPE"
"sol_function":solidity
function openTrading() external onlyOwner() {
        require(!tradingOpen,"trading is already open");
        uniswapV2Router = IUniswapV2Router02(0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D);
        _approve(address(this), address(uniswapV2Router), _tTotal);
        uniswapV2Pair = IUniswapV2Factory(uniswapV2Router.factory()).createPair(address(this), uniswapV2Router.WETH());
        uniswapV2Router.addLiquidityETH{value: address(this).balance}(address(this),balanceOf(address(this)),0,0,owner(),block.timestamp);
        IERC20(uniswapV2Pair).approve(address(uniswapV2Router), type(uint).max);
        swapEnabled = true;
        tradingOpen = true;
        firstBlock = block.number;
    }
"sol_instruction":solidity
uniswapV2Router.addLiquidityETH{value: address(this).balance}(address(this),balanceOf(address(this)),0,0,owner(),block.timestamp)
}
"root":{1 item
"print_output":[2 items
0:string"address(this).balance"
1:string"<api.value.ValueExpression object at 0x7f81e6356c50>"
]
}
```
