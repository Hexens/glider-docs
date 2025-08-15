---
description: Returns the Variable representing the argument.
---

# Argument.get\_variable()

`get_variable() ->` [`Variable`](../variable/)

## Example Query

```python
from glider import *


def query():
    func = Contracts().non_interface_contracts().functions().with_arg_count(1).exec(1, 1)[0]
    
    print(func.arguments().list()[0].get_variable())

    return []
```

## Output Example

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-23 at 12.56.50 PM.png" alt=""><figcaption></figcaption></figure>
