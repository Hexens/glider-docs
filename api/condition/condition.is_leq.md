---
description: Returns true if it is "<=" check, otherwise returns false.
---

# Condition.is\_leq()

```python
from glider import *

def query():
  functions = Functions().name_prefix('checkIf').exec(300)
  results = []
  uniq_source_code = []
  for func in functions:
    if_instructions = func.if_instructions() # api.instructions.IfInstruction's instance
    if(len(if_instructions) > 0):
      # this will be True if the comparition operators is less than or equal ("<=")
      is_leq = func.if_instructions()[0].get_condition().is_leq()
      source_code = func.if_instructions()[0].source_code()
      if is_leq and source_code not in uniq_source_code:
        uniq_source_code.append(source_code)
        print(func.if_instructions()[0].source_code())
        results.append(func)
  return results
```

Output:

```json
{
  "print_output": [
    "debtRatio_ <= MAX_DEBT_RATIO",
    "vesting[cachedIndexVesting[referrals[i].referralAddr] - 1].tokensReserved <= 1"
  ]
}
```
