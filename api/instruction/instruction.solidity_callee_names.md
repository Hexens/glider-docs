---
description: >-
  Returns the list of solidity function names that are called from the
  instruction. Returns a empty list if the instruction does not call any
  solidity function.
---

# Instruction.solidity\_callee\_names()

`solidity_callee_names() → List[str]`

Like [callee\_names()](instruction.callee_names.md) the function return list of called function names, but filtered to only built-in functions, like `require, assert, keccak256` etc.

## Query Example

```python
from glider import *
def query():

  instructions = Instructions().exec(1, 95)

  print(instructions[0].solidity_callee_names())
  
  return instructions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure>

