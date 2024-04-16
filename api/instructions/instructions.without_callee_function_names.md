# Instructions.without\_callee\_function\_names()

`without_callee_function_names(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Instructions`](./)

Adds a filter to get instructions that don't call a function with the given name.

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = (
    Instructions().
    without_callee_function_names(["transfer", "transferFrom"]).
    exec(1)
  )

  return instructions
```

## Output Example

```solidity
{
    "contract": "0xd705c24267ed3c55458160104994c55c6492dfcf"
    "contract_name": "Context"
    "sol_function": 
        function _msgSender() internal view virtual returns (address) {
                return msg.sender;
            }
    "sol_instruction":
        {
            return msg.sender;
        }

}
```
