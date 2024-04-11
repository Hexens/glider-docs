# Instruction.get\_dest()

Query

```python
from glider import *
def query():
  instruction = Instructions().exec(1,54)
  dests = instruction[0].get_dest()
  for dest in dests:
    print(dest.node.expression)
      
  return []
```

Output

```python
{
    "print_output": ["NEW VARIABLE owner = ERC721.ownerOf(tokenId)"]
}
```
