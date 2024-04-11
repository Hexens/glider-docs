---
description: >-
  Returns True if the instruction is a storage write instruction, else returns
  False. A storage write instruction writes to the state variable of a contract
---

# Instruction.is\_storage\_write()

Query

```python
from glider import *
def query():
  #fetch a list of instructions
  instructions = Instructions().exec(2,21) 
  for instruction in instructions:
   #print the source code of the instruction(Just to showcase the instruction too)
    print(instruction.source_code())
    #prints True/False depending on whether the instruction is a storage write instruction or not
    print(instruction.is_storage_write())
  return []
```

Output

```json
{"print_output": 
	[
		"_owner = newOwner", 
		"True", 
		"emit OwnershipTransferred(oldOwner,newOwner)", 
		"False"
	]
}
```

In the output above, the first instruction is a storage write instruction where the `_owner` state variable is written with the value of ``newOwner. Hence, the `is_storage_write()` returns `True` whereas for the second instruction it returns `False` as it does not write to any state variable``&#x20;
