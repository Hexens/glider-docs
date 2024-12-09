---
description: Returns metadata on all calls in the Instruction.
---

# Instruction.get\_callees()

`get_callees() → Dict`

## Query Example

```python
from glider import *

def query():
    instructions = Instructions().exec(3,182)
    results = []
    
    for inst in instructions: 
        print(inst.get_callees())

    return instructions
```

## Example Output

```solidity
[
  {
    ...
    "sol_instruction": 
        require(newOwner != address(0), \"Ownable: new owner is the zero address\")
  },
  {
    ...
    "sol_instruction": 
        _transferOwnership(newOwner)
  },
  {
    ...
    "sol_instruction": 
        onlyOwner
  },
  {
    "print_output": [
        {
            'internal': [], 
            'high_level': [], 
            'library_calls': [], 
            'low_level': [], 
            'solidity': [{
                'signature': 'require(bool,string)', 
                'return_type': [], 
                'type': 'call'
            }]
        }, {
            'internal': [{
                'signature': '_transferOwnership(address)', 
                'visibility': 'internal'
            }], 
            'high_level': [], 
            'library_calls': [], 
            'low_level': [], 
            'solidity': []
        }, {
            'internal': [{
                'signature': 'onlyOwner()', 
                'visibility': 'internal'
            }], 
            'high_level': [], 
            'library_calls': [], 
            'low_level': [], 
            'solidity': []
        }"
    ]
  }
]
```
