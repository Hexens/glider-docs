---
description: >-
  Returns the list of all points following the current point in the current data
  flow graph and outside of that.
---

# Instruction.forward\_df\_recursive()

`forward_df_recursive() →` [`APISet`](../iterables/apiset.md)`[`[`Point`](../point/)`]`

The function works similarly to [Instruction.forward\_df()](instruction.forward_df.md); the main difference is that in case of Instruction.forward\_df() the function will return forward dataflow point for every point in the Instruction, while Instruction.forward\_df() returns only those connected with the current Instruction.&#x20;

Like all other dataflow (DF) functions, it returns a list/set of Points, which can be instructions or "points" in the code, such as arguments, variables, etc.

## Query Example

```python
from glider import *

def query():
    # Fetch an instruction
    instructions = (
        Functions()
        .with_address("0xBC6e47b27f61531602662E3cC4DB688DB8cb7Ce8")
        .with_name("getInvariant")
        .exec(1)
        .instructions()
        .exec(1,2)

    )
    
    # Return the list of instructions following the current instruction
    instruction = instructions[0]

    # Iterate through each recursive point and print it's source code
    for point in instruction.forward_df_recursive():
        print(point.source_code())

    # Return the entry instruction to print all downstream points
    return instructions
```

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-17 at 2.50.45 PM.png" alt=""><figcaption></figcaption></figure>
