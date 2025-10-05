---
description: >-
  Returns a list of all instructions following the current point in the current
  data flow graph and outside of that
---

# Value.forward\_df\_recursive()

`forward_df_recursive() →` [`APISet`](../../iterables/apiset.md)`[`[`Point`](../../point/)`]`

The function works similarly to [Value.forward\_df()](value.forward_df.md); the main difference is that in case of Value.forward\_df() the function will return forward dataflow point for every point in the Value, while Value.forward\_df() returns only those connected with the current Value.&#x20;

Like all other dataflow (DF) functions, it returns a list/set of Points, which can be instructions or "points" in the code, such as arguments, variables, etc.

## Query Example

Consider the following Solidity function:

```solidity
function _removeTokenFromOwnerEnumeration(address from,uint256 tokenId) private {
    uint256 lastTokenIndex = _ownedTokens[from].length.sub(1);
    uint256 tokenIndex = _ownedTokensIndex[tokenId];
    if (tokenIndex != lastTokenIndex) {
        uint256 lastTokenId = _ownedTokens[from][lastTokenIndex];
        _ownedTokens[from][tokenIndex] = lastTokenId; 
        _ownedTokensIndex[lastTokenId] = tokenIndex; 
    }

    _ownedTokens[from].length--;
}
```

We want to check where the lastTokenIndex variable is used inside this function. To do this, we can query for the first instruction that assigns the lastTokenIndex:

```python
instructions = (
  Functions()
  .with_name("_removeTokenFromOwnerEnumeration")
  .instructions()
  .exec(1,1)
)
```

Once we get the lastTokenIndex variable:

```python
lastTokenIndex_variable = instruction.get_dest()
```

We can then call `forward_df_recursive()` which will return every point where lastTokenIndex is used:

```python
for point in assigned_variable.forward_df_recursive():
    print(point.source_code())
```

The full query can be found below:

```python
from glider import *


def query():
    instructions = (
      Functions()
      .with_name("_removeTokenFromOwnerEnumeration")
      .instructions()
      .exec(1,1)
    )

    for instruction in instructions:
        lastTokenIndex_variable = instruction.get_dest()
        for point in lastTokenIndex_variable.forward_df_recursive():
            print(point.source_code())

    return instructions
```

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-08 at 9.53.48 AM.png" alt=""><figcaption></figcaption></figure>
