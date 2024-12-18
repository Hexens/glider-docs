---
description: Returns an Arguments object for the arguments of the function/modifier.
---

# Callable.arguments()

`arguments() →` [`ArgumentPoints`](../point/argumentpoints/)

## Example

```python
from glider import *

def query():
    functions = Functions().exec(1,4)

    for func in functions:
        for arg in func.arguments().list():
            print(f"Function name: {func.name}, Argument: {arg.source_code()}")

    return functions

```

## Example output

<figure><img src="../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>



{% hint style="info" %}
The function returns ArgumentPoints, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
