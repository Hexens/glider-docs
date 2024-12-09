---
description: Returns the modifier's properties.
---

# Modifier.properties()

`properties() →` [`APIList`](../iterables/apilist.md)`[`[`MethodProps`](../callables/methodprop/)`]`

## Query Example

```python
from glider import *

def query():
  # Fetch a list of modifiers
  modifiers = Modifiers().exec(1)

  # Retrieve the properties of the first modifier
  properties = modifiers[0].properties()
  for prop in properties:
    print(prop)

  return modifiers
```

## Output Example

```solidity
{
  "content": [
    {
      "contract": "0xae690cf07c85bfb2de29ab32080c0ea182ae82b5",
      "contract_name": "REBITCOIN",
      "sol_modifier": solidity
        modifier onlyOwner() {
          if (msg.sender != owner) {
            throw;
          }
          _;
        },
      "sol_modifier_souce_line": 34
    },
    {
      "print_output": [
        "MethodProp.HAS_STATE_VARIABLES_READ"
      ]
    }
  ]
}
```
