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
    functions = Functions().exec(1,5)

    for function in functions:
        for call in function.callee_values():
            print(f"function {function.name}, call {call.expression}")

    return functions
```

## Example Output

<figure><img src="../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>
