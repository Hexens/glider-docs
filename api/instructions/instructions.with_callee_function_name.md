# Instructions.with\_callee\_function\_name()

`with_callee_function_name(name: str, sensitivity: bool = True) →` [`Instructions`](./)

Adds a filter to get [Instructions](./) that call a function with the given name.

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = (
    Instructions().
    with_callee_function_name("assert", sensitivity=False).
    exec(1)
  )

  return instructions
```

## Output Example

```solidity
{
    "contract": "0x23297ee054e8f600af482013ddbe856b7178a7d3"
    "contract_name": "MathHelpers"
    "sol_function":
        function divisionRoundedUp(
                uint256 numerator,
                uint256 denominator
            )
                internal
                pure
                returns (uint256)
            {
                assert(denominator != 0); // coverage-enable-line
                if (numerator == 0) {
                    return 0;
                }
                return numerator.sub(1).div(denominator).add(1);
        }
    "sol_instruction":
        assert(denominator != 0)

}
```
