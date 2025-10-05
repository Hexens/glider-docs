---
description: Returns the arguments of the call in key/value format
---

# Call.kv\_parameters()

`kv_parameters() → List[Tuple[`[`Argument`](../../argument/)`,` [`Value`](../)`]] | NoneObject`

The function is used to return argument information in a key/value format; it returns a list of tuples, where the first element is the argument of the function, and the second element is the value that is being passed as that argument.

The function is mainly used to account for the key/value format of function calls, e.g:

```solidity
return someFuncWithManyInputs({a: address(0), b: true, c: "c", x: 1, y: 2, z: 3});
```

but it can also be used with a regular call syntax.

## **Query Example**

```python
from glider import *

def query():
  instructions = Instructions().external_calls().exec(1)

  for instruction in instructions:
    for call in instruction.get_components():
      if isinstance(call, Call):
        for arg, val in call.kv_parameters():
          print(arg.source_code(), val.expression)

  return instructions
```

## **Example Output**

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-09 at 2.41.30 PM.png" alt=""><figcaption></figcaption></figure>
