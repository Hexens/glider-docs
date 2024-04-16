# Instructions.with\_callee\_function\_name\_suffix()

`with_callee_function_name_suffix(suffix: str, sensitivity: bool = True) →` [`Instructions`](./)

Adds a filter to get instructions that call a function whose name has the given suffix.

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = (
    Instructions().
    with_callee_function_name_suffix("dao", sensitivity=False).
    exec(1)
  )

  return instructions
```

## Output Example

```solidity
{
    "contract": "0x36b3382b8d215658d76f3526c999e55ea3b027a0"
    "contract_name": "LexDAORole"
    "sol_function":
        function addLexDAO(address account) public onlyLexDAO {
                _addLexDAO(account);
            }
    "sol_instruction": 
        _addLexDAO(account
}
```
