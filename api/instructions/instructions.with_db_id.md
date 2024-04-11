# Instructions.with\_db\_id()

**`with_db_id`**`(`_`db_id: str`_`) →` [`Instruction`](./)

Adds a filter to get instruction having given db id.

## Return type

`→` [`Instruction`](./)

```python
from glider import *

def query():
  # Fetch a list of instructions
  instructions = Instructions().exec(10)

  # Get the id of the first instruction
  db_id = instructions[0].db_id

  # Print the code of the first instruction for comparison
  print(instructions[0].source_code())

  # Get the instruction with given id
  instruction = Instructions().with_db_id(db_id)

  return [instruction]
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
    "print_output": [
      "{
  
          return msg.sender;
  
      }"
    ]
  }
]
```
