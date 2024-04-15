---
description: Returns the destination (lvalue) if the instruction has any type of assignment
---

# Instruction.get\_dest()

`get_dest() → List[Value]`

For the function:

```solidity
function log10(uint256 value) internal pure returns (uint256) {
        uint256 result = 0;
        unchecked {
            if (value >= 10 ** 64) {
                value /= 10 ** 64;
                result += 64;
            }
            if (value >= 10 ** 32) {
                value /= 10 ** 32;
                result += 32;
            }
            if (value >= 10 ** 16) {
                value /= 10 ** 16;
                result += 16;
            }
            if (value >= 10 ** 8) {
                value /= 10 ** 8;
                result += 8;
            }
            if (value >= 10 ** 4) {
                value /= 10 ** 4;
                result += 4;
            }
            if (value >= 10 ** 2) {
                value /= 10 ** 2;
                result += 2;
            }
            if (value >= 10 ** 1) {
                result += 1;
            }
        }
        return result;
    }
```

The instruction:

```solidity
result += 64;
```

Will return the `result` variable as an instance of Value-derived class, as the result is a variable, it will be of type Var.&#x20;

## Query Example

```python
from glider import *
def query():
  instruction = Instructions().exec(100,300)
  dests = instruction[0].get_dest()
  for dest in dests:
    print(dest.expression)
      
  return [instruction[0]]
```

## Output

```solidity
"root":{4 items
"contract":string"0xa4915dc6ee2652c471397c32ce5c8d3494ef3e6c"
"contract_name":string"Math"
"sol_function":solidity
function log10(uint256 value) internal pure returns (uint256) {
        uint256 result = 0;
        unchecked {
            if (value >= 10 ** 64) {
                value /= 10 ** 64;
                result += 64;
            }
            if (value >= 10 ** 32) {
                value /= 10 ** 32;
                result += 32;
            }
            if (value >= 10 ** 16) {
                value /= 10 ** 16;
                result += 16;
            }
            if (value >= 10 ** 8) {
                value /= 10 ** 8;
                result += 8;
            }
            if (value >= 10 ** 4) {
                value /= 10 ** 4;
                result += 4;
            }
            if (value >= 10 ** 2) {
                value /= 10 ** 2;
                result += 2;
            }
            if (value >= 10 ** 1) {
                result += 1;
            }
        }
        return result;
    }
"sol_instruction":solidity
result += 64
},
"root":{1 item
    "print_output":[1 item
    0:string"result"
    ]
}
```
