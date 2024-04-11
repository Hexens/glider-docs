# Instructions.with\_called\_function\_name\_suffix()

**`with_called_function_name_suffix`**`(`_`prefix: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Instructions`](./)

Adds a filter to get instructions that call a function whose name has the given suffix.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of intructions that call a function or modifier with suffix "From"
  instructions = Instructions().with_called_function_name_suffix("From").exec(1)

  return instructions
```

Output:

```json
{
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "ERC721",
  "sol_function": function safeTransferFrom(
        address from,address to,uint256 tokenId
    ) public virtual override {
        safeTransferFrom(from,to,tokenId,"");
    },
  "sol_instruction": safeTransferFrom(from,to,tokenId,"")
}
```
