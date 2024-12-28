# CatchInstruction.get\_block\_instructions()

`get_block_instructions() → List[`[`Instruction`](../)`]`

Returns all instructions from the catch block

## Query Example

```python
from glider import *

def query():
  instructionlist = Instructions().catch_instructions().exec(1,1)
  
  return instructionlist[0].get_block_instructions()
```

## Output Example&#x20;

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
