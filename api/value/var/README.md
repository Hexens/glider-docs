---
description: The class is used to represent a variable used in the instruction.
---

# Var

Var represents not just a variable in general but a specific "placement" of that variable in the code while the classes like [LocalVariable](../../localvariable/) or [StateVariable](../../statevariable/) etc. represent the variable itself.

Example:

```solidity
function addBots(address[] memory bots) public onlyOwner() {
        for (uint i = 0; i < bots.length; i++) {
            if (bots[i] != uniswapV2Pair && bots[i] != address(uniswapV2Router)) {
                isBot[bots[i]] = true;
            }
        }
    }
```

Here, the `bots`argument is used in different instructions, and each usage of the bots will be represented by a different Var, while the Argument object that can be retrieved using the get\_object\_of\_var() function will represent the `bots` in general as an argument.



`Bases:` [`Value`](../)`, Point`
