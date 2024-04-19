---
description: >-
  Returns the list of pairs, where the first element is the function and the
  second element is the argument to which data flow reaches from the argument
  (it may reach through a chain of calls).
---

# Argument.df\_reaching\_functions\_arguments()

`df_reaching_functions_arguments() → List[Tuple[`[`Callable`](../callable/)`, int]]`

```python
from glider import *
def query():
    func = Contracts().with_name('Pair').non_interface_contracts().functions().with_arg_count(5).exec(1)[0]
    arg = func.arguments().list()[0]
    
    results = [func]
    for (f, arg_index) in arg.df_reaching_functions_arguments():
        results.append(f)
        print(f.source_code() + '\n\n'+str(arg_index))
    return results
```

For the argument `uint256 lpTokenAmount` in the function `nftRemove` at address 0xf792e438b3bd8501274d98a58d19f2777cacd9f6

```solidity
function nftRemove(
        uint256 lpTokenAmount,
        uint256 minBaseTokenOutputAmount,
        uint256 deadline,
        uint256[] calldata tokenIds,
        bool withFee
    ) public returns (uint256 baseTokenOutputAmount, uint256 fractionalTokenOutputAmount) {
        // remove liquidity and send fractional tokens and base tokens to sender
        (baseTokenOutputAmount, fractionalTokenOutputAmount) =
            remove(lpTokenAmount, minBaseTokenOutputAmount, tokenIds.length * ONE, deadline);
 
        // unwrap the fractional tokens into NFTs and send to sender
        unwrap(tokenIds, withFee);
    }
```

The function will return tuples like this:

`[(removeQuote, 0), (remove, 0),...]`



```solidity
"root":{3 items
"contract":string"0xf792e438b3bd8501274d98a58d19f2777cacd9f6"
"contract_name":string"Pair"
"sol_function":solidity
function removeQuote(uint256 lpTokenAmount) public view returns (uint256, uint256) {
        uint256 lpTokenSupply = lpToken.totalSupply();
        uint256 baseTokenOutputAmount = (baseTokenReserves() * lpTokenAmount) / lpTokenSupply;
        uint256 fractionalTokenOutputAmount = (fractionalTokenReserves() * lpTokenAmount) / lpTokenSupply;
        uint256 upperFractionalTokenOutputAmount = (fractionalTokenReserves() * (lpTokenAmount + 1)) / lpTokenSupply;
 
        if (
            fractionalTokenOutputAmount % 1e18 != 0
                && upperFractionalTokenOutputAmount - fractionalTokenOutputAmount <= 1000 && lpTokenSupply > 1e15
        ) {
            fractionalTokenOutputAmount = upperFractionalTokenOutputAmount;
        }
 
        return (baseTokenOutputAmount, fractionalTokenOutputAmount);
    },
    
    
    function remove(
        uint256 lpTokenAmount,
        uint256 minBaseTokenOutputAmount,
        uint256 minFractionalTokenOutputAmount,
        uint256 deadline
    ) public returns (uint256 baseTokenOutputAmount, uint256 fractionalTokenOutputAmount) {
        // *** Checks *** //
 
        // check that the trade has not expired
        require(deadline == 0 || deadline >= block.timestamp, "Expired");
 
        // calculate the output amounts
        (baseTokenOutputAmount, fractionalTokenOutputAmount) = removeQuote(lpTokenAmount);
 
        // check that the base token output amount is greater than the min amount
        require(baseTokenOutputAmount >= minBaseTokenOutputAmount, "Slippage: base token amount out");
 
        // check that the fractional token output amount is greater than the min amount
        require(fractionalTokenOutputAmount >= minFractionalTokenOutputAmount, "Slippage: fractional token out");
 
        // *** Effects *** //
 
        // transfer fractional tokens to sender
        _transferFrom(address(this), msg.sender, fractionalTokenOutputAmount);
 
        // *** Interactions *** //
 
        // burn lp tokens from sender
        lpToken.burn(msg.sender, lpTokenAmount);
 
        if (baseToken == address(0)) {
            // if base token is native ETH then send ether to sender
            msg.sender.safeTransferETH(baseTokenOutputAmount);
        } else {
            // transfer base tokens to sender
            ERC20(baseToken).safeTransfer(msg.sender, baseTokenOutputAmount);
        }
 
        emit Remove(baseTokenOutputAmount, fractionalTokenOutputAmount, lpTokenAmount);
    },
    
    ...
```

As can be seen, the argument flows into function calls like:

<pre class="language-solidity"><code class="lang-solidity">remove(lpTokenAmount, minBaseTokenOutputAmount, tokenIds.length * ONE, deadline);

<strong>---> and inside remove():
</strong>
        (baseTokenOutputAmount, fractionalTokenOutputAmount) = removeQuote(lpTokenAmount);
...
</code></pre>

Returns: List\[Tuple\[[Callable](../callable/), int]]
