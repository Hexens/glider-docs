---
description: >-
  Returns the list of instructions following the current instruction till the
  branching point.
---

# Instruction.next\_block()

`next_block() → List[`[`Instruction`](./)`]`

Query

```python
from glider import *
def query():
  # get if-instructions (to showcase how the function works)
  instructions = Instructions().if_instructions().exec(1,100)
  # get the same function where we have if, get it entry point and call next_block
  entry_point = instructions[0].get_parent().entry_point_instructions().exec()[0]
  # we should get instructions from entry point of the function up to the first if-statement
  return instructions + entry_point.next_block()
```

Output

```solidity
"root":{4 items
"contract":string"0x5e6b2027f794a069bfa5e80195e22544d40ae600"
"contract_name":string"NATEHALLINAN"
"sol_function":solidity
function _transfer(
        address from,
        address to,
        uint256 amount
    ) internal override {
        require(from != address(0), "ERC20: transfer from the zero address");
        require(to != address(0), "ERC20: transfer to the zero address");
        require(!_blacklist[from] && !_blacklist[to], "You are a bot");

        if (amount == 0) {
            super._transfer(from, to, 0);
            return;
        }

        if (limitsInEffect){
            if (
                from != owner() &&
                to != owner() &&
                to != address(0) &&
                to != address(0xdead) &&
                !swapping
            ) {
          ....
          ....
    }
"sol_instruction":solidity
limitsInEffect
},
"sol_instruction":solidity
require(from != address(0), "ERC20: transfer from the zero address")
},
"sol_instruction":solidity
require(to != address(0), "ERC20: transfer to the zero address")
},
"sol_instruction":solidity
require(!_blacklist[from] && !_blacklist[to], "You are a bot")
},
"sol_instruction":solidity
amount == 0
}
```

The output shows that the query returns all the instructions in the \_setOwner() function
