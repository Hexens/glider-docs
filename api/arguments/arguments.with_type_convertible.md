---
description: >-
  Returns a list of arguments that can be converted to specified types.
  Convertor will define a table of allowed conversions.
---

# Arguments.with\_type\_convertible()

## Function Signature

`with_type_convertible(arg_type: List[str], convertor:` [`Convertor`](../convertor/)`) -> List[`[`Argument`](../argument/)`]`



## Query Example

```python
from glider import *

def query():
  # Create a Convertor object 
  convertor = Convertor()

  # Add a conversion from address to bytes20
  convertor.add("address", "bytes20")

  # Fetch a list of functions
  funs = Contracts().non_interface_contracts().functions().exec(20)

  # Return the functions with at least one argument convertible to bytes20
  # It will be only the argument of type address
  output = []
  for fun in funs:
    args = fun.arguments().with_type_convertible(["bytes20"], convertor)
    if args:
      output.append(fun)
  return output
```

## Output Example

```solidity
{
  "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf",
  "contract_name": "Token",
  "sol_function": "
    function balanceOf(address account) public view override returns (uint256) {
            return _balances[account];
    }
  "
}
```
