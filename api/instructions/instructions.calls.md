---
description: Returns an Instructions object for the call instructions
---

# Instructions.calls()

## Function Signature

`calls() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  # Fetch a list of call instructions
  instructions = Instructions().calls().exec(1)
  
  return instructions
```

## Output Example

```solidity
{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
    "contract_name": "SafeMath"
    "sol_function":
        function add(uint256 a, uint256 b) internal pure returns (uint256) {
                uint256 c = a + b;
                require(c >= a, "SafeMath: addition overflow");
                return c;
            }
    "sol_instruction":
        require(c >= a, "SafeMath: addition overflow")
}
```

This example returns the call instruction to the `require()` solidity built-in function.
