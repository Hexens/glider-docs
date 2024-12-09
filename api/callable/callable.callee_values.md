---
description: >-
  Returns a list of Call objects that represents called functions from the
  function/modifier.
---

# Callable.callee\_values()

`callee_values() →` [`APIList`](../iterables/apilist.md)`[`[`Call`](../value/call/)`]`

## Query Example

```python
from glider import *

def query():
    functions = Functions().exec(10)

    for function in functions:
        for call in function.callee_values():
            print(f"function {function.name}, call {call.expression}")

    return functions
```

## Example Output

```json
[
  ...
  {
    "print_output": [
      "function transfer, call Transfer(msg.sender,_to,_amount)",
      "function transferFrom, call Transfer(_from,_to,_amount)",
      "function approve, call Approval(msg.sender,_spender,_amount)",
      "function burn, call Burn(msg.sender,_value)",
      "function burnFrom, call Burn(_from,_value)"
    ]
  }
]
```
