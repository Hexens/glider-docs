---
description: Returns the arguments of the call in key/value format
---

# Call.kv\_parameters()

`kv_parameters() → List[Tuple[`[`Argument`](../argument/)`,` [`Value`](../value/)`]] | NoneObject`

The function is used to return argument information in a key/value format; it returns a list of tuples, where the first element is the argument of the function, and the second element is the value that is being passed as that argument.

The function is mainly used to account for the key/value format of function calls, e.g:

```solidity
return someFuncWithManyInputs({a: address(0), b: true, c: "c", x: 1, y: 2, z: 3});
```

but it can also be used with a regular call syntax.

&#x20;**Query Example**

```python
from glider import *

def query():
  instructions = Instructions().external_calls().exec(1)

  for instruction in instructions:
    for call in instruction.get_callee_values():
        for arg, val in call.kv_parameters():
          print(arg.source_code(), val.expression)

  return instructions
```

**Output**

```solidity
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Token"
"sol_function":solidity
constructor () {
        uniswapV2Pair = IUniswapV2Factory(uniswapV2Router.factory()).createPair(address(this), uniswapV2Router.WETH());
        _taxWallet = payable(_msgSender());
        _balances[_msgSender()] = _tTotal;
        _isExcludedFromFee[owner()] = true;
        _isExcludedFromFee[address(this)] = true;
        _isExcludedFromFee[_taxWallet] = true;
        _isExcludedFromFee[address(uniswapV2Router)] = true;
        _approve(msg.sender, address(this), type(uint256).max);
        _approve(address(this), address(uniswapV2Router), type(uint256).max);
        emit Transfer(address(0), _msgSender(), _tTotal);
    }
"sol_instruction":solidity
uniswapV2Pair = IUniswapV2Factory(uniswapV2Router.factory()).createPair(address(this), uniswapV2Router.WETH())
}
"root":{1 item
"print_output":[4 items
0:string"address tokenA"
1:string"this"
2:string"address tokenB"
3:string"uniswapV2Router.WETH()"
]
}
```
