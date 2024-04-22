---
description: Returns the call's qualifier (target) is exists
---

# Call.get\_call\_qualifier()

`get_call_qualifier() →` [`Value`](../) `| NoneObject`

The call's qualifier is the "target" of the call.

For example, for the call:

```solidity
uniswapV2Router.factory().createPair(address(this), uniswapV2Router.WETH())
```

The qualifier is the:

```solidity
uniswapV2Router.factory()
```

**Query Example**

```python
from glider import *

def query():
  instructions = Instructions().external_calls().exec(100)

  output = []

  for entry_ins in instructions:
    for call in entry_ins.get_callee_values():
        output.append(entry_ins)
        qualifier = call.get_call_qualifier()
        print(qualifier, qualifier.expression)
        return [entry_ins]

  return output
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
"print_output":[2 items
0:string"<api.value.Call object at 0x7fa78df02750>"
1:string"uniswapV2Router.factory()"
]
}
```

As can be seen in the example above, the qualifier itself is a call:

```solidity
uniswapV2Router.factory()
```

For that reason, the function has returned the value of type [Call](./).
