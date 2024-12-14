---
description: >-
  Returns the function that is being called, if exists, otherwise returns
  NoneObject
---

# Call.get\_function()

`get_function() →` [`Function`](../../callable/function/) `| NoneObject`

The function will return the [Function](../../callable/function/) object of the function being called, as there can be cases (such as low-level external calls, or solidity built-in calls) where there is no defined function the function will return NoneObject:

For example, in the call:

```solidity
require(balanceOf(to) + amount <= _maxWalletSize, "Exceeds the limit")
```

The if the function is used on the call representing the `require(...)`, NoneObject will be returned, as there is no solidity code representing the builtin function.

On the other hand if the function is called on the call representing `balanceOf(to)` it will return the [Function](../../callable/function/) object of the `balanceOf`.

{% hint style="info" %}
Note that for the external calls made using interfaces, the function will return the interface Function object.

For the call:

```solidity
IUniswapV2Factory(factory).createPair(address(this),uniswapV2Router.WETH())
```

it will return a function object representing the `IUniswapV2Factory` interface's `createPair` function
{% endhint %}

**Query Example**

```python
from glider import *

def query():
  instructions = Instructions().with_callee_function_name('require').exec(10)

  results = []
  for instruction in instructions:
    for call in instruction.get_callee_values():
      if not isinstance(call.get_function(),NoneObject):
        print(call.expression)
        results.append(call.get_function())
      else:
        print('no function object: ' + call.get_signature())

  return results
```

**Output Example**

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (2) (1).png" alt=""><figcaption></figcaption></figure>

### The function was called from the `_fallback()` instruction

<figure><img src="../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
