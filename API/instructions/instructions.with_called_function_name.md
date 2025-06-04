# Instructions.with\_called\_function\_name()

**`with_called_function_name`**`(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Instructions`](./)

Adds a filter to get instructions that call a function with the given name.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of instructions that call the "transfer" function
  instructions = Instructions().with_called_function_name("transfer").exec(1)

  return instructions
```

Output:

```json
{
  "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
  "contract_name": "Core",
  "sol_function": function allocateRing(address to,uint256 amount)
        external
        override
        onlyGovernor
    {
        IERC20 _ring = ring;
        require(
            _ring.balanceOf(address(this)) >= amount,"Core: Not enough Ring"
        );

        _ring.transfer(to,amount);

        emit RingAllocation(to,amount);
    },
  "sol_instruction": _ring.transfer(to,amount)
}
```
