---
description: >-
  Returns True if the instruction is a storage read instruction, else returns
  False. A storage read instruction just reads the value of a state variable
  without making any changes to it
---

# Instruction.is\_storage\_read()

Query

```python
from glider import *
def query():
  #fetch a list of instructions
  instructions = Instructions().exec(1,36) 
  for instruction in instructions:
   #print the source code of the instruction
    print(instruction.source_code())
    #prints True/False depending on whether the instruction is a storage read 
    #instruction or not
    print(instruction.is_storage_read())
  return []
```

Output

```json
{"print_output": 
	[
		"return _balances[owner]", 
		"True"
	]
}
```

In the output above, the instruction only reads the \_balances mapping, hence True is returned
