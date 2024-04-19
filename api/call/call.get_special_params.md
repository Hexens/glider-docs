---
description: Return the dict representing the special params of the call
---

# Call.get\_special\_params()

`get_special_params() → Dict[str, List[`[`Value`](../value/)`]]`

Some of the call types can have special parameters like `gas, salt, value`.  The function can be used to get a dict representing these values.

**Query Example**

```python
from glider import *

def query():
  instructions = Instructions().external_calls().exec(20,20)

  results =[]

  for instruction in instructions:
    for call in instruction.get_callee_values():
        special_params = call.get_special_params()
        if special_params['call_value']:
          results.append(instruction)
          print(call.get_special_params(), call.expression)

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
"root":{4 items
"contract":string"0x72e3142f8cf57ee0107f332fce18aca593735b1f"
"contract_name":string"ElonCat"
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
    }
"sol_instruction":solidity
uniswapV2Router.addLiquidityETH{value: address(this).balance}(address(this),balanceOf(address(this)),0,0,owner(),block.timestamp)
}
"root":{1 item
"print_output":[4 items
0:string"{'call_gas': [], 'call_salt': [], 'call_value': [<api.value.ValueExpression object at 0x7f0500c84750>]}"
1:string"uniswapV2Router.addLiquidityETH{value: address(this).balance}(address(this),balanceOf(address(this)),0,0,owner(),block.timestamp)"
2:string"{'call_gas': [], 'call_salt': [], 'call_value': [<api.value.ValueExpression object at 0x7f0500cd2990>]}"
3:string"uniswapV2Router.addLiquidityETH{value: address(this).balance}(address(this),balanceOf(address(this)),0,0,owner(),block.timestamp)"
]
}
```
