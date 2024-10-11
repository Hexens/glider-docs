# Value.expression

`property expression: str`

The property returns the "part" of the instruction that the Value represents.

**Query Example**

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1, 99)
    )
    for instruction in instructions:
        print(instruction.get_components()[0].expression)
    return instructions
```

**Output**

<figure><img src="../../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

Here the Value represents the `msg.sender` variable inside the `return msg.sender;` instruction.
