# Function.return\_tuple()

`return_tuple() → Tuple[Type, List[`[`Value`](../../value/) `|`[`NoneObject`](../../internal/noneobject/)`]]`

Returns the function's `return (type, value)` tuples.

## Example

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(1,4)

  for func in functions:
    # Retrieve the return instructions of the first function
    return_tuple = func.return_tuple()
    print(f"Type is - {return_tuple[0]}")
    for value in return_tuple[1]:
      print(value.expression)

  return functions
```



## Output

<figure><img src="../../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>
