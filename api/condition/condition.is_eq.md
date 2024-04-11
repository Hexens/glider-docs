---
description: Returns true if it is an equality check, otherwise returns false.
---

# Condition.is\_eq()

```python
from glider import *

def query():
  functions = Functions().name_prefix('checkIf').exec(5)
  for func in functions:
    if_instructions = func.if_instructions() # api.instructions.IfInstruction's instance
    if(len(if_instructions) > 0):
      print(func.if_instructions()[0].source_code())
      # this will print True if the comparition operators is equal ("==")
      print(func.if_instructions()[0].get_condition().is_eq())
  return functions
```

Outputs:

```
{
  "print_output": [
    "payGroup[i] == msg.sender",
    "True",
    "dexFactory != address(0)",
    "False",
    "size == 0",
    "True",
    "m_Bots[_address]",
    "False"
  ]
}
```
