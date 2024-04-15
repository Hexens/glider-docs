---
description: Returns an Instructions object for the 'expression' instructions.
---

# Instructions. expression\_instructions()

`expression_instructions() →` [`Instructions`](./)

In Glider, all objects lacking defined types, such as `IfInstruction`, `CatchInstruction`, `BreakInstruction`, etc., are considered `expressions`

## Query Example

```python
from glider import *

def query():
  instructions = Instructions().expression_instructions().exec(5)

  return instructions
```

## Output Example

```solidity
{
    {
        "contract":"0xd705c24267ed3c55458160104994c55c6492dfcf"
        "contract_name":"SafeMath"
        "sol_function":
            function add(uint256 a, uint256 b) internal pure returns (uint256) {
                uint256 c = a + b;
                require(c >= a, "SafeMath: addition overflow");
                return c;
            }
        "sol_instruction":
            require(c >= a, "SafeMath: addition overflow")
    },

    "contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
    "contract_name":string"SafeMath"
    "sol_function":solidity
function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b <= a, errorMessage);
        uint256 c = a - b;
        return c;
    }
    "sol_instruction":solidity
        require(b <= a, errorMessage)
}
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function mul(uint256 a, uint256 b) internal pure returns (uint256) {
        if (a == 0) {
            return 0;
        }
        uint256 c = a * b;
        require(c / a == b, "SafeMath: multiplication overflow");
        return c;
    }
"sol_instruction":solidity
require(c / a == b, "SafeMath: multiplication overflow")
}
39
40
41
42
43
44
45
46
47
48
49
50
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"SafeMath"
"sol_function":solidity
function div(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256) {
        require(b > 0, errorMessage);
        uint256 c = a / b;
        return c;
    }
"sol_instruction":solidity
require(b > 0, errorMessage)
}
51
52
53
54
55
56
57
58
59
60
61
62
"root":{4 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Ownable"
"sol_function":solidity
constructor () {
        address msgSender = _msgSender();
        _owner = msgSender;
        emit OwnershipTransferred(address(0), msgSender);
    }
"sol_instruction":solidity
_owner = msgSender

```
