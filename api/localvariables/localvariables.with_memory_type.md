---
description: Returns the list of local variables having specified memory type.
---

# LocalVariables.with\_memory\_type()

`with_memory_type(memory_type: str) → List[`[`LocalVariable`](../localvariable/)`]`

**Query Example**

```python
from glider import *
def query():
  funcs = Functions().exec(1000)

  for func in funcs:
    local_vars = func.local_variables().with_memory_type('storage')
    for local_var in local_vars:
      print(local_var.name)
      print(local_var.type.name)
      return [local_var.get_parent()]

  return []
```

**Output**

```solidity
"root":{3 items
"contract":string"0x72e3142f8cf57ee0107f332fce18aca593735b1f"
"contract_name":string"ElonCat"
"sol_function":solidity
function claim(uint256 id) external {
        Node storage node = nodes[msg.sender][id];
        uint256 timeElapsed = block.timestamp - node.lastClaimTime;
        node.lastClaimTime = block.timestamp;
        _balances[msg.sender] =
            _balances[msg.sender] +
            timeElapsed *
            rewardPerSecond;
    }
}
"root":{1 item
"print_output":[2 items
0:string"node"
1:string"Node"
]
}
```
