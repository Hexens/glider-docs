# Instructions.with\_callee\_function\_signature()

`with_callee_function_signature(signature: str) →` [`Instructions`](./)

Adds a filter to get instructions that call a function with the given signature.

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = (
    Instructions().
    with_callee_function_signature("deposit(uint256)").
    exec(1)
  )

  return instructions
```

## Output Example

```solidity
{
    "contract": "0x8113c706de48acf6aec7960abc9a3652ed2434c5"
    "contract_name": "OneSplitIearn"
    "sol_function":
        function _iearnSwap(
                IERC20 fromToken,
                IERC20 destToken,
                uint256 amount,
                uint256[] memory distribution,
                uint256 flags
            ) private {
                if (fromToken == destToken) {
                    return;
                }
        
                if (flags.check(FLAG_DISABLE_ALL_WRAP_SOURCES) == flags.check(FLAG_DISABLE_IEARN)) {
                    IIearn[13] memory yTokens = _yTokens();
        
                    for (uint i = 0; i < yTokens.length; i++) {
                        if (fromToken == IERC20(yTokens[i])) {
                            IERC20 underlying = yTokens[i].token();
                            yTokens[i].withdraw(amount);
                            _iearnSwap(underlying, destToken, underlying.balanceOf(address(this)), distribution, flags);
                            return;
                        }
                    }
        
                    for (uint i = 0; i < yTokens.length; i++) {
                        if (destToken == IERC20(yTokens[i])) {
                            IERC20 underlying = yTokens[i].token();
                            super._swap(fromToken, underlying, amount, distribution, flags);
        
                            uint256 underlyingBalance = underlying.balanceOf(address(this));
                            underlying.universalApprove(address(yTokens[i]), underlyingBalance);
                            yTokens[i].deposit(underlyingBalance);
                            return;
                        }
                    }
                }
        
                return super._swap(fromToken, destToken, amount, distribution, flags);
        }
    "sol_instruction":
        yTokens[i].deposit(underlyingBalance)
}
```
