---
description: Returns the Instructions object withe all the external call instructions.
---

# Instructions.external\_calls()

**`external_calls`**`() →` [`Instructions`](./)

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  # Fetch a list of external call instructions
  instructions = Instructions().external_calls().exec(1)
  
  return instructions
```

## Output Example

```solidity
{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
    "contract_name": "Token"
    "sol_function":
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
    "sol_instruction":
        uniswapV2Pair = IUniswapV2Factory(uniswapV2Router.factory()).createPair(address(this), uniswapV2Router.WETH())
}

```
