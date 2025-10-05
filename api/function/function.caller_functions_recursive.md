---
description: >-
  Returns a Functions object representing the functions which are called from
  the function
---

# Function.caller\_functions\_recursive()

`caller_functions_recursive() ->` [`Functions`](../callables/functions/)

The function is the _**extended**_**/**_**inter-procedural**_ variant of function caller\_functions, meaning it works recursively. It returns the Functions object representing all the functions that are eventually called from within the function.&#x20;

The difference between `caller_functions_recursive()` and `caller_functions()` is that the latter one will only return directly called functions, while the recursive version will find all the functions recursively that eventually get called from the target function.

## Query Example

```python
from glider import *


def query():
    functions = Functions().with_name('depositToken').exec(1,10)

    #lets take the first function from the result and return its extended_caller_functions
    output = functions[0].caller_functions_recursive().exec()

    #print the code of the function, to be aware of whose callers we get
    print(functions[0].source_code())

    return output
```

## Example Output

#### Source code of depositToken :

```solidity
function depositToken() public view returns (address) {
    return getAddress(_DEPOSIT_TOKEN_SLOT);
}
```

#### Source code of extended caller functions:

```solidity
function depositCurve() internal {
    uint256 tokenBalance = IERC20(depositToken()).balanceOf(address(this));
    IERC20(depositToken()).safeApprove(curveDeposit(), 0);
    IERC20(depositToken()).safeApprove(curveDeposit(), tokenBalance);

    // we can accept 0 as minimum, this will be called only by trusted roles
    uint256 minimum = 0;
    if (nTokens() == 2) {
      uint256[2] memory depositArray;
      depositArray[depositArrayPosition()] = tokenBalance;
      ICurveDeposit_2token(curveDeposit()).add_liquidity(depositArray, minimum);
    } else if (nTokens() == 3) {
      uint256[3] memory depositArray;
      depositArray[depositArrayPosition()] = tokenBalance;
      ICurveDeposit_3token(curveDeposit()).add_liquidity(depositArray, minimum);
    } else if (nTokens() == 4) {
      uint256[4] memory depositArray;
      depositArray[depositArrayPosition()] = tokenBalance;
      if (metaPool()) {
        ICurveDeposit_4token_meta(curveDeposit()).add_liquidity(underlying(), depositArray, minimum);
      } else {
        ICurveDeposit_4token(curveDeposit()).add_liquidity(depositArray, minimum);
      }
    }
  }

```

```solidity
function _liquidateReward() internal {
    if (!sell()) {
      // Profits can be disabled for possible simplified and rapoolId exit
      emit ProfitsNotCollected(sell(), false);
      return;
    }

    for(uint256 i = 0; i < rewardTokens.length; i++){
      address token = rewardTokens[i];
      uint256 rewardBalance = IERC20(token).balanceOf(address(this));
      if (rewardBalance == 0 || storedLiquidationDexes[token][weth].length < 1) {
        continue;
      }

      uint256 toHodl = rewardBalance.mul(hodlRatio()).div(hodlRatioBase);
      if (toHodl > 0) {
        IERC20(token).safeTransfer(hodlVault(), toHodl);
        rewardBalance = rewardBalance.sub(toHodl);
        if (rewardBalance == 0) {
          continue;
        }
      }
      IERC20(token).safeApprove(universalLiquidator(), 0);
      IERC20(token).safeApprove(universalLiquidator(), rewardBalance);
      // we can accept 1 as the minimum because this will be called only by a trusted worker
      ILiquidator(universalLiquidator()).swapTokenOnMultipleDEXes(
        rewardBalance,
        1,
        address(this), // target
        storedLiquidationDexes[token][weth],
        storedLiquidationPaths[token][weth]
      );
    }

    uint256 rewardBalance = IERC20(weth).balanceOf(address(this));

    notifyProfitInRewardToken(rewardBalance);
    uint256 remainingRewardBalance = IERC20(rewardToken()).balanceOf(address(this));

    if (remainingRewardBalance == 0) {
      return;
    }

    IERC20(rewardToken()).safeApprove(universalLiquidator(), 0);
    IERC20(rewardToken()).safeApprove(universalLiquidator(), remainingRewardBalance);

    // we can accept 1 as minimum because this is called only by a trusted role
    ILiquidator(universalLiquidator()).swapTokenOnMultipleDEXes(
      remainingRewardBalance,
      1,
      address(this), // target
      storedLiquidationDexes[weth][depositToken()],
      storedLiquidationPaths[weth][depositToken()]
    );

    uint256 tokenBalance = IERC20(depositToken()).balanceOf(address(this));
    if (tokenBalance > 0) {
      depositCurve();
    }
  }

```

```solidity
function doHardWork() external onlyNotPausedInvesting restricted {
    IBaseRewardPool(rewardPool()).getReward();
    _liquidateReward();
    investAllUnderlying();
  }

```

```solidity
function withdrawAllToVault() public restricted {
    if (address(rewardPool()) != address(0)) {
      exitRewardPool();
    }
    _liquidateReward();
    IERC20(underlying()).safeTransfer(vault(), IERC20(underlying()).balanceOf(address(this)));
  }
```
