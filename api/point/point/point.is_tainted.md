---
description: Returns whether the point is tainted.
---

# Point.is\_tainted()

A point is considered tainted when it is influenced by an external input such as user input.

## Query Example

Consider the following Solidity function:

```solidity
function stake(
    address _to,uint256 _amount,bool _rebasing,bool _claim
) external returns (uint256) {
    miner.safeTransferFrom(msg.sender,address(this),_amount);
    _amount = _amount.add(rebase()); 
    if (_claim && warmupPeriod == 0) {
        return _send(_to,_amount,_rebasing);
    } else {
        Claim memory info = warmupInfo[_to];
        if (!info.lock) {
            require(_to == msg.sender,"External deposits for account are locked");
        }

        warmupInfo[_to] = Claim({
            deposit: info.deposit.add(_amount),gons: info.gons.add(vMINER.gonsForBalance(_amount)),expiry: epoch.number.add(warmupPeriod),lock: info.lock
        });

        gonsInWarmup = gonsInWarmup.add(vMINER.gonsForBalance(_amount));

        return _amount;
    }
}
```

In this function, we want to determine if the following line is influenced by user input:

<pre class="language-solidity"><code class="lang-solidity"><strong>gonsInWarmup = gonsInWarmup.add(vMINER.gonsForBalance(_amount));
</strong></code></pre>

We know that `_amount` comes from a function argument, which is user-controlled. Therefore, this line of code is influenced by user input, and therefore tainted.

To write a query to confirm this, we first query the components in the instruction and call `is_tainted()` against any of the Points.

```python
from glider import *


def query():
    return (
        Contracts()
        .with_name("MinerStaking")
        .exec(1)
        .functions()
        .with_name("stake")
        .exec(1)
        .instructions()
        .expression_instructions()
        .exec()
        .filter(lambda instruction : "gonsInWarmup" in instruction.get_dest().expression)
        .filter(is_tainted)
    )


def is_tainted(instruction):
    components = instruction.get_components()
    for component in components:
        for df in component.backward_df():
            if df.is_tainted():
                return True

    return False                

```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-16 at 5.25.41 PM.png" alt=""><figcaption></figcaption></figure>
