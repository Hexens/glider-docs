# Instructions.calls()

**calls**() → [Instructions](./)

Returns an [Instructions](./) object for the call instructions.

## Return type

→ [Instructions](./)

```python
from glider import *

def query():
  # Fetch a list of call instructions
  instructions = Instructions().calls().exec(1)
  
  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "constructor() {
        _setOwner(_msgSender());
    }",
  "sol_instruction": "_setOwner(_msgSender())"
}
```

This example returns the call instruction to the `_setOwner()` private function.
