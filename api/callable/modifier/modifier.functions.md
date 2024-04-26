# Modifier.functions()

`functions() →` [`Functions`](../../callables/functions/)

Returns the [Functions](../../callables/functions/) object for the functions which have the modifier.



An example to retrieve the functions object for the modifier is as below

```python
from glider import *
def query():
  modifierlist = Modifiers()\
      .with_name_prefix("check")\
      .exec(1)
  
  results =  []

  for modd in modifierlist:
    for funcs in modd.functions().exec():
      results.append(funcs)

  return results
```

## Output

```solidity
"root":{3 items
"contract":string"0x15a4a47e85aa36fe4ee68e35eedb6bc10489f4af"
"contract_name":string"UnipilotActiveVault"
"sol_function":solidity
function readjustLiquidity() external override onlyOperator checkDeviation {
        _pulled = 1;
        ReadjustVars memory a;
 
        (uint128 totalLiquidity, , ) = pool.getPositionLiquidity(
            ticksData.baseTickLower,
            ticksData.baseTickUpper
        );
 
        (a.amount0Desired, a.amount1Desired, a.fees0, a.fees1) = pool
            .burnLiquidity(
                ticksData.baseTickLower,
                ticksData.baseTickUpper,
                address(this)
            );
 
        transferFeesToIF(true, a.fees0, a.fees1);
 
        int24 baseThreshold = tickSpacing * getBaseThreshold();
        (, a.currentTick, ) = pool.getSqrtRatioX96AndTick();
 
        (a.tickLower, a.tickUpper) = UniswapLiquidityManagement.getBaseTicks(
            a.currentTick,
            baseThreshold,
            tickSpacing
        );
 
        if (
            (totalLiquidity > 0) &&
            (a.amount0Desired == 0 || a.amount1Desired == 0)
        ) {
            bool zeroForOne = a.amount0Desired > 0 ? true : false;
 
            int256 amountSpecified = zeroForOne
                ? int256(FullMath.mulDiv(a.amount0Desired, 50, 100))
                : int256(FullMath.mulDiv(a.amount1Desired, 50, 100));
 
            pool.swapToken(address(this), zeroForOne, amountSpecified);
        } else {
            a.amount0Desired = _balance0();
            a.amount1Desired = _balance1();
 
            a.liquidity = pool.getLiquidityForAmounts(
                a.amount0Desired,
                a.amount1Desired,
                a.tickLower,
                a.tickUpper
            );
 
            (a.amount0, a.amount1) = pool.getAmountsForLiquidity(
                a.liquidity,
                a.tickLower,
                a.tickUpper
            );
 
            a.zeroForOne = UniswapLiquidityManagement.amountsDirection(
                a.amount0Desired,
                a.amount1Desired,
                a.amount0,
                a.amount1
            );
 
            a.amountSpecified = a.zeroForOne
                ? int256(
                    FullMath.mulDiv(a.amount0Desired.sub(a.amount0), 50, 100)
                )
                : int256(
                    FullMath.mulDiv(a.amount1Desired.sub(a.amount1), 50, 100)
                );
 
            pool.swapToken(address(this), a.zeroForOne, a.amountSpecified);
        }
 
        a.amount0Desired = _balance0();
        a.amount1Desired = _balance1();
 
        (ticksData.baseTickLower, ticksData.baseTickUpper) = pool
            .getPositionTicks(
                a.amount0Desired,
                a.amount1Desired,
                baseThreshold,
                tickSpacing
            );
 
        pool.mintLiquidity(
            ticksData.baseTickLower,
            ticksData.baseTickUpper,
            a.amount0Desired,
            a.amount1Desired
        );
    }
}
```

