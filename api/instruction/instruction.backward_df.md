---
description: >-
  Returns a list of all previous instructions/arguments of the current point in
  the data flow graph.
---

# Instruction.backward\_df()

## Function Signature

`backward_df() → List[Point]`

The `backward_df()` function is an intra-procedural analysis function. This means that the function does not operate recursively and instead returns `instructions/arguments` within the current function instruction set.

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
