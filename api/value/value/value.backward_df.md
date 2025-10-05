---
description: >-
  Returns a list of all previous instructions/arguments of the current point in
  the data flow graph.
---

# Value.backward\_df()

`backward_df() ->` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../../point/)`]`

The function works similarly to [Instruction.backward\_df()](../../instruction/instruction.backward_df.md); the main difference is that in case of Instruction.backward\_df() the function will return backward dataflow point for every point in the Value, while Value.backward\_df() returns only those connected with the current Value.&#x20;

Like all other dataflow (DF) functions, it returns a list/set of Points, which can be instructions or "points" in the code, such as arguments, variables, etc.

## Query Example

Consider the following Solidity function:

```solidity
function _transfer(address sender,address recipient,uint256 amount) internal virtual {
    require(sender != address(0),"ERC20: transfer from the zero address");
    require(recipient != address(0),"ERC20: transfer to the zero address");
    
    _beforeTokenTransfer(sender,recipient,amount);
    
    uint256 senderBalance = _balances[sender];
    require(senderBalance >= amount,"ERC20: transfer amount exceeds balance");
    _balances[sender] = senderBalance - amount;
    _balances[recipient] += amount;
    
    emit Transfer(sender,recipient,amount);
}
```

In this function, we want to locate the first require statement and determine the origin of the sender variable:

```solidity
require(sender != address(0),"ERC20: transfer from the zero address");
```

To do this, we first query for the instruction containing the require statement and then query for sender.

Finally, we call backward\_df() to identify where sender originates.

```python
from glider import *


def query():
    instructions = (
      Functions()
      .with_name('_transfer')
      .instructions()
      .exec(1, 1)
    )

    for instruction in instructions:
        for component in instruction.get_components():
            print(component)

            print("Value: " + component.expression)
            for point in component.backward_df():
                print(point.source_code())

    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-03 at 2.57.18 PM.png" alt=""><figcaption></figcaption></figure>
