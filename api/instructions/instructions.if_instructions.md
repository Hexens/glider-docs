---
description: Returns an Instructions object for the 'if' instructions.
---

# Instructions.if\_instructions()

**`if_instructions()`**` ``→` [`Instructions`](./)

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  # Fetch a list of if statement instructions
  instructions = Instructions().if_instructions().exec(2)

  return instructions
```

## Output Example

```solidity
{
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
        "contract_name": "SafeMath"
        "sol_function":
            function mul(uint256 a, uint256 b) internal pure returns (uint256) {
                    if (a == 0) {
                        return 0;
                    }
                    uint256 c = a * b;
                    require(c / a == b, "SafeMath: multiplication overflow");
                    return c;
            }
        "sol_instruction":solidity
            a == 0
    },
    {
        "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
        "contract_name": "Token"
        "sol_function":
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
        "sol_instruction":
            !_isExcludedFromFee[from] && !_isExcludedFromFee[to]       
    }
}
```

Note that the ternary operator is included as well.
