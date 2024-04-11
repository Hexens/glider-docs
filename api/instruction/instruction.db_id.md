# Instruction.db\_id

Returns the unique id of an instruction in the glider database

Query

```python
from glider import *
def query():
  #fetch an instruction
  instructions = Instructions().exec(1,16)
  #print the db_id of an instruction
  print(instructions[0].db_id) 
  return []
```

Output

```json
{
    "print_output": ["instructions/3e43450b9ca1f0ac4516b0b4177d825f"]
}
```
