# Convertor.set\_conversions()

**`set_conversions`**`(`_`conversions: dict`_`) → None`

Set allowed conversions.

Deletes any previous conversions added to the [Convertor](./).\
Takes as an argument a dictionary with as keys the convertible types and as values the lists of allowed converted types.

```python
from glider import *

def query():
  # Create a Convertor object 
  convertor = Convertor()

  # Set conversion from address to bytes20
  convertor.set_conversions({"bytes20": ["address", "uint160"]})

  # Fetch a list of functions
  funs = Functions().exec(10)

  # Return the functions with at least one argument converitble to bytes20
  # It will be only the argument of type address
  output = []
  for fun in funs:
    args = fun.arguments().with_type_convertible(["bytes20"], convertor)
    if args:
      output.append(fun)
  return output
```

Output (first result only):

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "function transferOwnership(address newOwner) public virtual onlyOwner {\n        require(newOwner != address(0),\"Ownable: new owner is the zero address\");\n        _setOwner(newOwner);\n    }"
}
```
