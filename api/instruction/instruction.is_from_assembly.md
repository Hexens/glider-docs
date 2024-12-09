---
description: >-
  Returns true if the instruction is from assembly block, otherwise returns
  false.
---

# Instruction.is\_from\_assembly()

`is_from_assembly() -> bool`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(500,500)
        .filter(lambda inst : inst.is_from_assembly())
    )
    
    return instructions
```

## Output Example

```solidity
[
  {
    "contract": "0xe5fA13058EdE558a2bFA675043f175148858A5F6",
    "contract_name": "StakeMaster",
    "contract_link": "",
    "uuid": "11ef2556-13c3-4a42-9f78-f9fcf8bde7fc",
    "severity": "",
    "sol_function": 
       function isContract(address _addr) private view returns (bool) {
            uint32 size;
            assembly {
                size := extcodesize(_addr)
            }
            return (size > 0);
        }
    "sol_instruction": 
        assembly {
            size := extcodesize(_addr)
        }
  },
  {
    "contract": "0xe5fA13058EdE558a2bFA675043f175148858A5F6",
    "contract_name": "StakeMaster",
    "contract_link": "",
    "uuid": "a9e4254a-dad2-4d71-ac62-c464a66caf1f",
    "severity": "",
    "sol_function":
       function isContract(address _addr) private view returns (bool) {
            uint32 size;
            assembly {
                size := extcodesize(_addr)
            }
            return (size > 0);
        }
    "sol_instruction": 
        size := extcodesize(_addr)
  },
  {
    "contract": "0xe5fA13058EdE558a2bFA675043f175148858A5F6",
    "contract_name": "StakeMaster",
    "contract_link": "",
    "uuid": "5039f28d-d16a-4f1c-b87f-6dd4098f8d77",
    "severity": "",
    "sol_function": 
       function isContract(address _addr) private view returns (bool) {
            uint32 size;
            assembly {
                size := extcodesize(_addr)
            }
            return (size > 0);
        }
    "sol_instruction": 
        assembly {
            size := extcodesize(_addr)
        }
  }
]
```
