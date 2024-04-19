# Value.parent\_value

Returns the parent [Value](./) in case the current one is inside another Value; returns None otherwise.

`property parent_value:` [`Value`](./) `| None`

**Query Example**

```python
from glider import *
def query():
	instructions = Instructions().exec(1,105)
	calls = instructions[0].get_callee_values()
	for call in calls:
		for arg in call.get_args():
			print(arg.expression)
			print(arg.parent_value.expression)
	return instructions
```

**Output**

```solidity
"root":{4 items
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
"sol_instruction":solidity
emit Transfer(from, address(this),taxAmount)
}
"root":{1 item
"print_output":[6 items
0:string"from"
1:string"Transfer(from,address(this),taxAmount)"
2:string"this"
3:string"Transfer(from,address(this),taxAmount)"
4:string"taxAmount"
5:string"Transfer(from,address(this),taxAmount)"
]
}
```
