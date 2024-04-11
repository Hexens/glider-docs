---
description: >-
  Returns a list of all previous instructions/arguments of the current point in
  the data flow graph. Intraprocedural
---

# Argument.backward\_df()

As Argument has no intraprocedural backward dataflow, this function solely exists to comply with the glider architecture, but if used will return an empty list

```python
from glider import *
def query():
    func = Contracts().non_interface_contracts().functions().with_arg_count(1).exec(1)[0]
    for ins in func.arguments().list()[0].backward_df():
        print(ins.source_code())
    return [func]
```

```json
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Token"
"sol_function":solidity
function balanceOf(address account) public view override returns (uint256) {
        return _balances[account];
    }
}
```
