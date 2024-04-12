---
description: Returns true if it is "<=" check, otherwise returns false.
---

# Condition.is\_leq()

```python
from glider import *

def query():
  if_instructions = Instructions().if_instructions().exec(100,200)

  for if_instruction in if_instructions:
    if if_instruction.get_condition().is_leq():
      print(if_instruction.source_code())
      return [if_instruction.get_parent()]
  return []
```

Output:

```solidity
"root":{3 items
"contract":string"0x8a93bc8ed29da1b090265137a9d201ebf1154626"
"contract_name":string"MerkleProof"
"sol_function":solidity
function processProof(bytes32[] memory proof, bytes32 leaf) internal pure returns (bytes32) {
        bytes32 computedHash = leaf;
        for (uint256 i = 0; i < proof.length; i++) {
            bytes32 proofElement = proof[i];
            if (computedHash <= proofElement) {
                // Hash(current computed hash + current element of the proof)
                computedHash = _efficientHash(computedHash, proofElement);
            } else {
                // Hash(current element of the proof + current computed hash)
                computedHash = _efficientHash(proofElement, computedHash);
            }
        }
        return computedHash;
    }
},
"root":{1 item
"print_output":[1 item
0:string"computedHash <= proofElement"
]
}
```
