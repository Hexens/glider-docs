---
description: Returns true if it is ">=" check, otherwise returns false.
---

# Condition.is\_geq()

```python
from glider import *

def query():
  functions = Functions().name_prefix('checkIf').exec(200)
  results = []
  for func in functions:
    if_instructions = func.if_instructions() # api.instructions.IfInstruction's instance
    if(len(if_instructions) > 0):
      # this will be True if the comparition operators is greater than or equal (">=")
      is_geq = func.if_instructions()[0].get_condition().is_geq()
      if is_geq:
        print(func.if_instructions()[0].source_code())
        results.append(func)
  return results
```



Output:

```
{
  "print_output": [
    "block.timestamp >= nd2GivingDeadline",
    "True",
    "m_Bots[_address] >= 2",
    "True"
  ]
}
```
