---
description: >-
  Returns a LocalVariables object for the local variables of the
  function/modifier.
---

# Callable.local\_variables()

`local_variables() →` [`LocalVariables`](../localvariables/)

## Query Example

```python
from glider import *
def query():
    functions = Functions().exec(1, 70)

    for function in functions:
        for local_var in function.local_variables().list():
            print(local_var.name)

    return functions
```

## Output Example

```solidity
[
  {
    "contract": "0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "contract_name": "MerkleProof",
    "contract_link": "https://etherscan.io/address/0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "uuid": "40943496-d2a9-4331-b2eb-f0f5d469d6d8",
    "severity": "",
    "sol_function": 
      function processMultiProof(
              bytes32[] memory proof,
              bool[] memory proofFlags,
              bytes32[] memory leaves
          ) internal pure returns (bytes32 merkleRoot) {
              // This function rebuild the root hash by traversing the tree up from the leaves. The root is rebuilt by
              // consuming and producing values on a queue. The queue starts with the `leaves` array, then goes onto the
              // `hashes` array. At the end of the process, the last hash in the `hashes` array should contain the root of
              // the merkle tree.
              uint256 leavesLen = leaves.length;
              uint256 totalHashes = proofFlags.length;
      
              // Check proof validity.
              require(leavesLen + proof.length - 1 == totalHashes, "MerkleProof: invalid multiproof");
      
              // The xxxPos values are "pointers" to the next value to consume in each array. All accesses are done using
              // `xxx[xxxPos++]`, which return the current value and increment the pointer, thus mimicking a queue's "pop".
              bytes32[] memory hashes = new bytes32[](totalHashes);
              uint256 leafPos = 0;
              uint256 hashPos = 0;
              uint256 proofPos = 0;
              // At each step, we compute the next hash using two values:
              // - a value from the "main queue". If not all leaves have been consumed, we get the next leaf, otherwise we
              //   get the next hash.
              // - depending on the flag, either another value for the "main queue" (merging branches) or an element from the
              //   `proof` array.
              for (uint256 i = 0; i < totalHashes; i++) {
                  bytes32 a = leafPos < leavesLen ? leaves[leafPos++] : hashes[hashPos++];
                  bytes32 b = proofFlags[i] ? leafPos < leavesLen ? leaves[leafPos++] : hashes[hashPos++] : proof[proofPos++];
                  hashes[i] = _hashPair(a, b);
              }
      
              if (totalHashes > 0) {
                  return hashes[totalHashes - 1];
              } else if (leavesLen > 0) {
                  return leaves[0];
              } else {
                  return proof[0];
              }
          }
        },
  {
    "print_output": [
      "i",
      "leafPos",
      "hashPos",
      "proofPos",
      "leavesLen",
      "hashes",
      "a",
      "b",
      "totalHashes"
    ]
  }
]
```
