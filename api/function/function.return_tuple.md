# Function.return\_tuple()

Returns the function's `return (type, value)` tuples.

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(10)

  # Retrieve the return instructions of the first function
  tuple_list = functions[0].return_tuple()

  return tuple_list
```

\


Output:

```json
[
  "address",
  ""
]
```
