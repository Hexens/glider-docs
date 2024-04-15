---
description: Returns an Instructions object for the 'continue' instructions
---

# Instructions. continue\_instructions()

`continue_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().continue_instructions().exec(1)
  
  return instructions
```

## Output Example

```solidity
{
    "contract": "0x8113c706de48acf6aec7960abc9a3652ed2434c5"
    "contract_name": "OneSplit"
    "sol_function":
        function swap(
                IERC20 fromToken,
                IERC20 destToken,
                uint256 amount,
                uint256 minReturn,
                uint256[] memory distribution,
                uint256 flags  // See constants in IOneSplit.sol
            ) public payable returns(uint256 returnAmount) {
                if (fromToken == destToken) {
                    return amount;
                }
        
                function(IERC20,IERC20,uint256,uint256)[DEXES_COUNT] memory reserves = [
                    _swapOnUniswap,
                    _swapOnNowhere,
                    _swapOnBancor,
                    _swapOnOasis,
                    _swapOnCurveCompound,
                    _swapOnCurveUSDT,
                    _swapOnCurveY,
                    _swapOnCurveBinance,
                    _swapOnCurveSynthetix,
                    _swapOnUniswapCompound,
                    _swapOnUniswapChai,
                    _swapOnUniswapAave,
                    _swapOnMooniswap,
                    _swapOnUniswapV2,
                    _swapOnUniswapV2ETH,
                    _swapOnUniswapV2DAI,
                    _swapOnUniswapV2USDC,
                    _swapOnCurvePAX,
                    _swapOnCurveRenBTC,
                    _swapOnCurveTBTC,
                    _swapOnDforceSwap,
                    _swapOnShell,
                    _swapOnMStableMUSD,
                    _swapOnCurveSBTC,
                    _swapOnBalancer1,
                    _swapOnBalancer2,
                    _swapOnBalancer3,
                    _swapOnKyber1,
                    _swapOnKyber2,
                    _swapOnKyber3,
                    _swapOnKyber4,
                    _swapOnMooniswapETH,
                    _swapOnMooniswapDAI,
                    _swapOnMooniswapUSDC
                ];
        
                require(distribution.length <= reserves.length, "OneSplit: Distribution array should not exceed reserves array size");
        
                uint256 parts = 0;
                uint256 lastNonZeroIndex = 0;
                for (uint i = 0; i < distribution.length; i++) {
                    if (distribution[i] > 0) {
                        parts = parts.add(distribution[i]);
                        lastNonZeroIndex = i;
                    }
                }
        
                if (parts == 0) {
                    if (fromToken.isETH()) {
                        msg.sender.transfer(msg.value);
                        return msg.value;
                    }
                    return amount;
                }
        
                fromToken.universalTransferFrom(msg.sender, address(this), amount);
                uint256 remainingAmount = fromToken.universalBalanceOf(address(this));
        
                for (uint i = 0; i < distribution.length; i++) {
                    if (distribution[i] == 0) {
                        continue;
                    }
        
                    uint256 swapAmount = amount.mul(distribution[i]).div(parts);
                    if (i == lastNonZeroIndex) {
                        swapAmount = remainingAmount;
                    }
                    remainingAmount -= swapAmount;
                    reserves[i](fromToken, destToken, swapAmount, flags);
                }
        
                returnAmount = destToken.universalBalanceOf(address(this));
                require(returnAmount >= minReturn, "OneSplit: Return amount was not enough");
                destToken.universalTransfer(msg.sender, returnAmount);
                fromToken.universalTransfer(msg.sender, fromToken.universalBalanceOf(address(this)));
            }
    "sol_instruction":
        continue

}
```
