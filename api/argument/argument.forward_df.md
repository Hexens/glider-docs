---
description: >-
  Returns a list of all instructions following the current point in the current
  data flow graph.
---

# Argument.forward\_df()

`forward_df() → List[`[`Instruction`](../instruction/)`]`

## Example Query

```python
from glider import *
def query():
    func = Contracts().non_interface_contracts().functions().with_arg_count(1).exec(1)[0]
    instrs = []
    for ins in func.arguments().list()[0].forward_df():
        instrs.append(ins)
    return instrs
```

## Output

```solidity
{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
    "contract_name": "Token",
    "sol_function": "
        function balanceOf(address account) public view override returns (uint256) {
            return _balances[account];
        }
    ",
    "sol_instruction": "
        return _balances[account]
    "
}
```
