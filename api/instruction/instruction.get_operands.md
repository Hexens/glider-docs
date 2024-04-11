# Instruction.get\_operands()

Query

```python
from glider import *
def query():
  instruction = Instructions().exec(1,54)
  #print the expression of the first operand returned by get_operands()
  print(instruction[0].get_operands()[0].expression)
  return []
```

Output

```json
{
    "print_output": ["ERC721.ownerOf(tokenId)"]
}
```
