---
description: >-
  Returns a list of all previous instructions/arguments/variables of the current
  point in the data flow graph.
---

# Instruction.backward\_df()

`backward_df() → List[Point]`

The `backward_df()` function is an intra-procedural analysis function. This means that the function does not operate recursively and instead returns `instruction/argument/variable` within the current function instruction set.

The function returns the derived classes from Point, such as [Argument](../argument/), Var, [Instruction](./).

## Query Example

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().with_callee_function_name('verify').exec(1)
  
  for points in instructions[0].backward_df():
    print(points.source_code())
  # return the list of previous instructions of the current instruction
  return instructions
```

## Output Example

```solidity
{
    {
        "contract": "0x8a93bc8ed29da1b090265137a9d201ebf1154626"
        "contract_name": "METAANIxKPP"
        "sol_function":
            function _verify(bytes32 leaf, bytes32[] memory proof)
                internal view returns (bool)
                {
                    return MerkleProof.verify(proof, allowListRoot, leaf);
                }
        "sol_instruction":
            return MerkleProof.verify(proof, allowListRoot, leaf)
    },
    {
        "print_output":[
            0: "bytes32 leaf"
            1: "bytes32[] proof"
            2: "return MerkleProof.verify(proof, allowListRoot, leaf)"
        ]
    }
}
```

For the same contract, this query showcases that the return list elements are type-casted from Point:

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().with_callee_function_name('verify').exec(1)
  
  for points in instructions[0].backward_df():
    if isinstance(points, Argument):
      print(points.name)
    print(points.source_code())
  # return the list of previous instructions of the current instruction
  return instructions
```

```solidity
"root":{1 item
    "print_output":[5 items
    0:string"return MerkleProof.verify(proof, allowListRoot, leaf)"
    1:string"leaf"
    2:string"bytes32 leaf"
    3:string"proof"
    4:string"bytes32[] proof"
    ]
}
```

