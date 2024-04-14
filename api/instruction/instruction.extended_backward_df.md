---
description: >-
  Returns a list of all previous instructions/arguments/variables of the current
  node in the current data flow graph and outside of this.
---

# Instruction.extended\_backward\_df()

The `extended_backward_df()` function is an inter-procedural analysis function. This means that the function operates recursively and returns `instruction/argument/variable` across the contract's functions.

The function returns the derived classes from Point, such as [Argument](../argument/), Var, [Instruction](./).

## Query Example

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().with_callee_function_name('verify').exec(1)
  
  for points in instructions[0].extended_backward_df():
    print(points.source_code())
  # return the list of previous instructions of the current instruction
  return instructions
```

## Output

```solidity
"root":{4 items
"contract":string"0x8a93bc8ed29da1b090265137a9d201ebf1154626"
"contract_name":string"METAANIxKPP"
"sol_function":solidity
function _verify(bytes32 leaf, bytes32[] memory proof)
    internal view returns (bool)
    {
        return MerkleProof.verify(proof, allowListRoot, leaf);
    }
"sol_instruction":solidity
return MerkleProof.verify(proof, allowListRoot, leaf)
}
"root":{1 item
"print_output":[15 items
    0:string"bytes32[] proof"
    1:string"address account"
    2:string"uint256 amount"
    3:string"address account"
    4:string"return MerkleProof.verify(proof, allowListRoot, leaf)"
    5:string"address account"
    6:string"uint256 amount"
    7:string"bytes32[] proof"
    8:string"_verify(_leaf(account, amount), proof)"
    9:string"bytes32 leaf"
    10:string"require(checkredeem( account , amount , proof ) > 0 , "account is not in allowlist")"
    11:string"require(checkredeem( account , amount , proof ) > 0 , "account is not in allowlist")"
    12:string"bytes32[] proof"
    13:string"bytes32[] proof"
    14:string"uint256 amount"
]
}
```

For the same contract, this query showcases that the return list elements are type-casted from Point:

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().with_callee_function_name('verify').exec(1)
  
  for points in instructions[0].extended_backward_df():
    if isinstance(points, Argument):
      print("Argument name: " + points.name)
  # return the list of previous instructions of the current instruction
  return instructions
```

```solidity
"root":{1 item
    "print_output":[11 items
    0:string"Argument name: leaf"
    1:string"Argument name: account"
    2:string"Argument name: account"
    3:string"Argument name: amount"
    4:string"Argument name: account"
    5:string"Argument name: amount"
    6:string"Argument name: amount"
    7:string"Argument name: proof"
    8:string"Argument name: proof"
    9:string"Argument name: proof"
    10:string"Argument name: proof"
    ]
}
```
