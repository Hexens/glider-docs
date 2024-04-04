# Instructions.with\_ids()

**`with_ids`**`(`_`ids: List[str]`_`) →` [`Instructions`](./)

Adds a filter to get instructions having ids from the given list.

## Return type

`→` [`Instructions`](./)

```python
from glider import *

def query():
  # Fetch a list of instructions
  instructions = Instructions().exec(10)

  # Define list of instruction ids
  db_ids = []

  # Add ids of 2 first instructions to list
  for instruction in instructions[:2]:
    # get id of instruction
    db_ids.append(instruction.db_id)

    # Print the instruction code for comparison
    print(instruction.source_code())

  # Get the instruction with given ids
  instructions = Instructions().with_ids(db_ids).exec()

  return instructions
```

Output:

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": function _msgSender() internal view virtual returns (address) {

        return msg.sender;

    },
    "sol_instruction": {

        return msg.sender;

    }
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": function _msgSender() internal view virtual returns (address) {

        return msg.sender;

    },
    "sol_instruction": return msg.sender
  },
  {
    "print_output": [
      "{

        return msg.sender;

     }",
      "return msg.sender"
    ]
  }
]
```
