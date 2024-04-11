# Arguments.with\_type\_convertible()

Returns a list of arguments that can be converted to specified types. Convertor will define a table of allowed conversions.

```python
from glider import *

def query():
  # Create a Convertor object 
  convertor = Convertor()

  # Add a conversion from address to bytes20
  convertor.add("address", "bytes20")

  # Fetch a list of functions
  funs = Functions().exec(10)

  # Return the functions with at least one argument convertible to bytes20
  # It will be only the argument of type address
  output = []
  for fun in funs:
    args = fun.arguments().with_type_convertible(["bytes20"], convertor)
    if args:
      output.append(fun)
  return output
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "function transferOwnership(address newOwner) public virtual onlyOwner {\n        require(newOwner != address(0),\"Ownable: new owner is the zero address\");\n        _setOwner(newOwner);\n    }"
}
```
