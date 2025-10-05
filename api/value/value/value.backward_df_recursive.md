---
description: >-
  Returns the list of all previous points of the current point in the current
  data flow graph and outside of that.
---

# Value.backward\_df\_recursive()

`backward_df_recursive() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../../point/)`]`&#x20;

The function works similarly to [Value.backward\_df()](value.backward_df.md); the main difference is that in case of Value.backward\_df() the function will return backward dataflow point for every point in the Value, while Value.backward\_df() returns only those connected with the current Value.&#x20;

Like all other dataflow (DF) functions, it returns a list/set of Points, which can be instructions or "points" in the code, such as arguments, variables, etc.

## Query Example

Consider the following Solidity functions:

<pre class="language-solidity"><code class="lang-solidity">function transfer(address recipient,uint256 amount) public virtual override returns (bool) {
        _transfer(_msgSender(),recipient,amount);
        return true;
}
    
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
}

<strong>function _transfer(address sender,address recipient,uint256 amount) internal virtual {
</strong>        require(sender != address(0),"ERC20: transfer from the zero address");
        require(recipient != address(0),"ERC20: transfer to the zero address");
        
        _beforeTokenTransfer(sender,recipient,amount);
        
        uint256 senderBalance = _balances[sender];
        require(senderBalance >= amount,"ERC20: transfer amount exceeds balance");
        _balances[sender] = senderBalance - amount;
        _balances[recipient] += amount;
        
        emit Transfer(sender,recipient,amount);
}
</code></pre>

In the \_transfer function, we want to locate the first require statement and determine the origin of the sender variable across multiple functions:

```solidity
require(sender != address(0),"ERC20: transfer from the zero address");
```

To do this, we first query for the instruction containing the require statement and then query for sender:

```python
instructions = (
  Functions()
  .with_name('_transfer')
  .instructions()
  .exec(1, 1)
)
```

Finally, we call backward\_df\_recursive() to identify where the sender originates. Glider will transverse from the \_transfer() function, transfer() function, and msgSender() functions to identify the sender source.

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
            print("Value: " + component.expression)
            for point in component.backward_df_recursive():
                print(point.source_code())

    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-04 at 3.15.48 PM.png" alt=""><figcaption></figcaption></figure>
