# Instructions.low\_level\_calls()

**`low_level_calls`**`() →` [`Instructions`](./)

Returns a list of the functions calls instructions.

Only solidity's low level `call()` is returned.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of low level calls instructions instructions
  instructions = Instructions().low_level_calls().exec(1)

  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Address",
  "sol_function": function sendValue(address payable recipient,uint256 amount) internal {
        require(address(this).balance >= amount,"Address: insufficient balance");

        (bool success,) = recipient.call{value: amount}("");
        require(success,"Address: unable to send value,recipient may have reverted");
    },
  "sol_instruction": (bool success,) = recipient.call{value: amount}("")
}
```
