---
description: >-
  Returns the list of function names that are called from the instruction. It
  returns an empty list for an instruction that does not call any functions
---

# Instruction.callee\_names()

`callee_names() → List[str]`

For example, for the instruction:

```solidity
require(!_exists(tokenId), "ERC721: token already minted");
```

The functions will return `['_exists', 'require']`

## Query Example

```python
from glider import *


def query():
  # Fetch an instruction
  instruction = Instructions().with_callee_name('require').exec(1,30)
  
  # Print the list of function names called from the instruction
  print(instruction[0].callee_names()) 
  return instruction
```

## Example Output

<figure><img src="../../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>
