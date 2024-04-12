# Function.properties()

Returns the function's properties as a list of [MethodProps](../methodprop/)

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(10)

  # Retrieve the properties of the first function
  properties = functions[0].properties()
  for prop in properties:
    print(prop)

  return functions
```

\


Output:

```json
{
  "print_output": [
    "MethodProp.IS_VIEW",
    "MethodProp.INTERNAL"
  ]
}
```
