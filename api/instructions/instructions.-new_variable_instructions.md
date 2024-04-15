# Instructions. new\_variable\_instructions()

Returns an [Instructions](./) object for the 'new variable' instructions

`new_variable_instructions() →` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().new_variable_instructions().exec(1)

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
        uint256 c = a + b
}
```
