---
description: Return the dict representing the special params of the call
---

# Call.get\_special\_params()

`get_special_params() → Dict[str, List[`[`Value`](../)`]]`

Some of the call types can have special parameters like `gas, salt, value`.  The function can be used to get a dict representing these values.

## **Query Example**

```python
from glider import *

def query():
  instructions = (
    Instructions()
    .external_calls()
    .exec(10,20)
    .filter(lambda instruction : instruction.get_parent().name == "_disperseEth")
  )

  results =[]

  for instruction in instructions:
    for call in instruction.get_components():
        if isinstance(call, Call):
          special_params = call.get_special_params()
          if special_params['call_value']:
            results.append(instruction)
            print(call.get_special_params(), call.expression)
    
  return results
```

## **Example Output**

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 2.38.45 PM.png" alt=""><figcaption></figcaption></figure>
