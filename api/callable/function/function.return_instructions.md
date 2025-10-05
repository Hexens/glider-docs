# Function.return\_instructions()

`return_instructions() →` [`Instructions`](../../instructions/)

Returns the `return` instructions of the function.

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(20)

  # Retrieve the return instructions of the first function
  instruction = functions[0].return_instructions().exec()

  return instruction
```

\


Output:

<figure><img src="../../../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>
