---
description: Returns true if it is ">" check, otherwise returns false.
---

# Condition.is\_gr()

```python
from glider import *

def query():
  functions = Functions().name_prefix('checkIf').exec(200)
  results = []
  for func in functions:
    if_instructions = func.if_instructions() # api.instructions.IfInstruction's instance
    if(len(if_instructions) > 0):
      # this will be True if the comparition operators is greater than (">")
      is_gr = func.if_instructions()[0].get_condition().is_gr()
      if is_gr:
        print(func.if_instructions()[0].source_code())
        results.append(func)
  return results
```



Ouput:

```
{
  "print_output": [
    "arts[_traitId][_rarityId].length > 0",
    "arts[_traitId][_rarityId].length > 0"
  ]
}
```
