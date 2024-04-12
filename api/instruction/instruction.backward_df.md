# Instruction.backward\_df()

`backward_df() → List[Point]`

Returns a list of all previous instructions/arguments of the current point in the data flow graph.



Query

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

Output

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
},
"root":{1 item
    "print_output":[3 items
    0:string"return MerkleProof.verify(proof, allowListRoot, leaf)"
    1:string"bytes32[] proof"
    2:string"bytes32 leaf"
    ]
}
```
