---
description: Returns true if it is "<" check, otherwise returns false.
---

# Condition.is\_le()

```python
from glider import *

def query():
  functions = Functions().name_prefix('checkIf').exec(200)
  results = []
  for func in functions:
    if_instructions = func.if_instructions() # api.instructions.IfInstruction's instance
    if(len(if_instructions) > 0):
      # this will be True if the comparition operators is less than ("<")
      is_le = func.if_instructions()[0].get_condition().is_le()
      if is_le:
        print(func.if_instructions()[0].source_code())
        results.append(func)
  return results
```



Output:

```
{
  "print_output": [
    "(address token0,address token1) = tokenA < tokenB ? (tokenA,tokenB) : (tokenB,tokenA)"
  ]
}
```
