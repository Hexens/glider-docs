---
description: >-
  Returns the list of pairs, where the first element is the function and the
  second element is the argument number from which data flow reaches the
  argument (it may reach through a chain of calls).
---

# Argument.df\_reaches\_from\_functions\_arguments()

`df_reaches_from_functions_arguments() → List[Tuple[`[`Callable`](../callable/)`, int]]`

```python
from glider import *
def query():
    func = Contracts().non_interface_contracts().functions().with_arg_count(1).exec(1)[0]
    arg = func.arguments().list()[0]
    
    results = [func]
    for (f, arg_index) in arg.df_reaches_from_functions_arguments():
        results.append(f)
        print(f.source_code() + '\n\n'+str(arg_index))
    return results
```

For the argument **account** of the function **balanceOf**:

```solidity
function balanceOf(address account) public view override returns (uint256) {
        return _balances[account];
    }
```

The query will return:

`[(_transfer, 1), .... ]`

```json
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Token"
"sol_function":solidity
function balanceOf(address account) public view override returns (uint256) {
        return _balances[account];
    }
}
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Token"
"sol_function":solidity
function _transfer(address from, address to, uint256 amount) private {
        uint256 taxAmount=0;
        if (!_isExcludedFromFee[from] && !_isExcludedFromFee[to]) {
            require(tradeOpen, "Trading not open");
            taxAmount = amount.mul((_buyCount>_reduceBuyTaxAt)?_finalBuyTax:_initialBuyTax).div(100);

            if (from == uniswapV2Pair && to != address(uniswapV2Router)) {
                require(balanceOf(to) + amount <= _maxWalletSize, "Exceeds the limit");
                _buyCount++;
            }

            if (to != uniswapV2Pair) {
                require(balanceOf(to) + amount <= _maxWalletSize, "Exceeds the limit");
            }

            if(to == uniswapV2Pair && from!= address(this) ){
                taxAmount = amount.mul((_buyCount>_reduceSellTaxAt)?_finalSellTax:_initialSellTax).div(100);
            }

            uint256 contractTokenBalance = balanceOf(address(this));
            if (!inSwap && to == uniswapV2Pair && swapEnabled && contractTokenBalance>_taxSwapThreshold) {
                swapTokensForEth(min(amount,min(contractTokenBalance,_maxTaxSwap)));
                uint256 contractETHBalance = address(this).balance;
                if(contractETHBalance > 0) {
                    sendETHToFee(address(this).balance);
                }
            }
        }

        if(taxAmount>0){
          _balances[address(this)]=_balances[address(this)].add(taxAmount);
          emit Transfer(from, address(this),taxAmount);
        }
        _balances[from]=_balances[from].sub(amount);
        _balances[to]=_balances[to].add(amount.sub(taxAmount));
        emit Transfer(from, to, amount.sub(taxAmount));
    }
}
...
```

As you can see the `address to` argument flows into multiple calls to `balanceOf(to)`**,** like:

```solidity
require(balanceOf(to) + amount <= _maxWalletSize, "Exceeds the limit");
```

Returns Type: List\[Tuple\[[Callable](../callable/), int]]
