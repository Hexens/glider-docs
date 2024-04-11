---
description: Returns a dictionary containing data about the instruction.
---

# Instruction.instruction\_data

Query

```python
from glider import *
def query():
  #fetch an instruction
  instruction = Instructions().exec(1)
  #print an instruction's instruction_data dict
  print(instruction[0].instruction_data)
  return []
```

Output

```json
{
  "print_output": [
    "{'_key': '80af75b7003ddd45de34a5c189a5c1d1', '_id': 'instructions/80af75b7003ddd45de34a5c189a5c1d1', '_rev': '_h_ZmbGe---', 'node': 'ENTRY_POINT', 'id': 0, 'type': 'NodeType.ENTRYPOINT', 'irs': [], 'irs_ssa': [], 'from_asm': False, 'is_cmp': False, 'source_lines': [19, 20, 21], 'start_column': 67, 'end_column': 6, 'callees': {'internal': [], 'high_level': [], 'library_calls': [], 'low_level': [], 'solidity': []}, 'dest': [], 'operands': [], 'variables_read': [], 'variables_written': [], 'dominators': [0], 'immediate_dominator': [], 'dominator_successors': [1], 'dominance_frontier': []}"
  ]
}
```
