# Instruction.get\_operand()

Query

```python
from glider import *
def query():
  instruction = Instructions().exec(1,54)
  print(instruction[0].get_operand(0).expression)
  return []
```

Output

```json
{
    "print_output": ["ERC721.ownerOf(tokenId)"]
}
```
