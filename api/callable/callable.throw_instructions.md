---
description: Returns throw instructions of the function/modifier.
---

# Callable.throw\_instructions()

`throw_instructions() →` [`Instructions`](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(10000)

  throw_instructions = []
  for function in functions:
    for instruction in function.throw_instructions().exec():
      # Return the throw instructions for each function
      throw_instructions.append(instruction)

  return throw_instructions
```

## Example output



```solidity
"root":{4 items
"contract":string"0x6c4c4759659d644cb36df4842a7f113321e3f7bb"
"contract_name":string"SafeMath"
"sol_function":solidity
function assert(bool assertion) internal {
    if (!assertion) throw;
  }
"sol_instruction":solidity
throw
}
```
