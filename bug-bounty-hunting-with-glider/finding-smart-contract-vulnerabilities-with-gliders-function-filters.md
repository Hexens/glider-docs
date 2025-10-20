---
icon: '2'
cover: ../.gitbook/assets/Frame 1.png
coverY: 0
---

# Finding Smart Contract Vulnerabilities with Glider’s Function Filters

## Introduction

Smart contract audits often involve large codebases where small mistakes can lead to serious consequences. Manually checking every function is not only time-consuming but also can lead to overlooking subtle issues.

Glider provides a practical way to reduce this complexity. By using its **function filtering** features, auditors can quickly find functions that match certain signatures, check whether modifiers are present, and trace how functions are called.

Most importantly, these queries are reusable. Once a vulnerability has been identified in one project, the same Glider query can be run against other smart contracts to quickly check if they suffer from the same weakness.

### How Glider’s Function Filtering Works <a href="#how-gliders-function-filtering-works" id="how-gliders-function-filtering-works"></a>

Glider exposes a `Functions()` query object that lets you slice and dice functions in a smart contract. Some of the tricks that auditors find most useful are:

* **`with_signature()`** – grab functions by their exact signature, e.g. `get_p(uint256)`.
* **`without_modifier_name()`** – find functions missing a critical modifier, like `onlyPoolManager`.
* **`caller_functions()`** – trace back to see who’s actually calling a given function.
* **`instructions()`** – look inside functions to check if they actually contain code (useful for ignoring empty stubs).
* **`exec()`** – run the query and get results back.

It feels a bit like writing database queries, but for Solidity code. With the right filters, you can zero in on suspicious logic that deserves a closer look.

### Case Study 1: UwuLend Oracle Bug <a href="#case-study-1-uwulend-oracle-bug" id="case-study-1-uwulend-oracle-bug"></a>

#### What Happened

Back in 2024, UwuLend was hacked because of how it used a Curve pool function called `get_p`. On the surface, `get_p` looks like a handy oracle—it gives you the spot price of a token in the pool. The problem is that this number is **easily manipulated** by shifting the pool’s reserves.

UwuLend relied on it as if it were a trustworthy price feed. Attackers quickly figured out that by pushing the pool around, they could make their collateral look way more valuable than it actually was, then borrow against it. The end result: the protocol was drained.

In short, UwuLend confused **spot price** with **fair price**, and the attackers cashed in on that mistake.

#### The Glider Query <a href="#the-glider-query" id="the-glider-query"></a>

With Glider, we can catch contracts making this exact mistake by asking: “Who’s calling `get_p(uint256)`?”

```
from glider import *

def query():
    return (
        Functions()
        .with_signature("get_p(uint256)")
        .exec()
        .caller_functions()
        .exec()
    )
```

This query first finds the `get_p` function, then traces out to every function that calls it. The results give you a neat shortlist of potential problem areas to inspect. Instead of combing through all contract logic, you go straight to the risky spots.

### Case Study 2: Cork UniswapV4 Hook Attack

#### What Happened <a href="#what-happened7" id="what-happened7"></a>

Uniswap V4 introduced **hooks**, which provide a way for protocols to plug in custom logic around pool events like swaps. It’s powerful, but it also means developers have to be very careful with access control.

Cork Protocol missed a step. Their `beforeSwap` hook didn’t use Uniswap’s `onlyPoolManager` modifier, which is supposed to make sure only the PoolManager can trigger it. Without that safeguard, attackers could call the hook directly, tamper with swap behavior, and walk away with more than **$10 million**.

It’s a classic case of “we thought no one would ever call this function directly,” and in DeFi, that’s always a dangerous assumption.

#### The Glider Query <a href="#the-glider-query8" id="the-glider-query8"></a>

To hunt for this kind of mistake, we can search for `beforeSwap` hooks that don’t have the `onlyPoolManager` modifier attached:

```
def query():
    return (
        Functions()
        .with_signature("beforeSwap(address,PoolKey,IPoolManager.SwapParams,bytes)")
        .without_modifier_name("onlyPoolManager")
        .exec()
        .filter(lambda func : len(func.instructions().exec()) > 0)
    )
```

This query is doing three things:

1. Look for any `beforeSwap` hooks.
2. Exclude the ones that are protected by `onlyPoolManager`.
3. Ignore empty functions, so we only focus on real implementations.

What you end up with is a precise hit list of hooks that are exposed to attack.

## Wrapping Up <a href="#wrapping-up" id="wrapping-up"></a>

Both UwuLend and Cork fell victim to mistakes that look obvious in hindsight: trusting an unsafe oracle and forgetting a simple modifier. But when you’re staring at a giant codebase, these issues are surprisingly easy to miss.

Glider’s **function filtering** helps flip the script. Instead of searching line by line, you can write a few queries and immediately highlight suspicious patterns:

* UwuLend: _“Who’s calling `get_p`?”_
* Cork: _“Which hooks forgot `onlyPoolManager`?”_

It doesn’t replace human judgment, but it gives auditors a powerful lens to focus their attention where it matters most.

If you want to explore more real examples or try similar checks yourself, visit the [Glider Query Database](https://r.xyz/glider-query-database). You’ll find a growing collection of public queries shared by researchers and auditors.

## Appendix: Incident Deep Dive <a href="#appendix-incident-deep-dive" id="appendix-incident-deep-dive"></a>

### UwuLend Oracle Bug <a href="#uwulend-oracle-bug" id="uwulend-oracle-bug"></a>

The UwuLend exploit happened because the protocol treated Curve’s `get_p` function as a reliable oracle. The function itself simply returns the spot price of a token, which can be manipulated by temporarily adjusting the liquidity pool balance.

```
sUSDePriceProviderBUniCatch.sol(0xd252953818bdf8507643c237877020398fa4b2e8)

  function getPrice() external view override returns (uint256) {
    (uint256[] memory prices, bool uniFail) = _getPrices(true);
    uint256 median = uniFail ? (prices[5] + prices[6]) / 2 : prices[5];
    require(median > 0, 'Median is zero');
    return FullMath.mulDiv(median, sUSDeScalingFactor, 1e3);
  }

  function _getPrices(bool sorted) internal view returns (uint256[] memory, bool uniFail) {
    uint256[] memory prices = new uint256[](11);
    (prices[0], prices[1]) = _getUSDeFraxEMAInUSD();
    (prices[2], prices[3]) = _getUSDeUsdcEMAInUSD();
    (prices[4], prices[5]) = _getUSDeDaiEMAInUSD();
    (prices[6], prices[7]) = _getCrvUsdUSDeEMAInUSD();
    (prices[8], prices[9]) = _getUSDeGhoEMAInUSD();
    try UNI_V3_TWAP_USDT_ORACLE.getPrice() returns (uint256 price) {
      prices[10] = price;
    } catch {
      uniFail = true;
    }
    if (sorted) {
      _bubbleSort(prices);
    }
    return (prices, uniFail);
  }

  function _getUSDeFraxEMAInUSD() internal view returns (uint256, uint256) {
    uint256 price = uwuOracle.getAssetPrice(FRAX);
    return (
      FullMath.mulDiv(FRAX_POOL.price_oracle(0), price, 1e18),
      FullMath.mulDiv(FRAX_POOL.get_p(0), price, 1e18) 
    );
  }

```

Here, the `_getUSDeFraxEMAInUSD` can be distorted through short-term manipulation of the Curve pool.

By inflating the collateral value, attackers were able to borrow more than they should, draining the protocol.

Spot prices from AMMs are not safe for lending oracles. Protocols should use **time-weighted average prices (TWAPs)** or external oracle feeds.

### Cork UniswapV4 Hook Attack <a href="#cork-uniswapv4-hook-attack" id="cork-uniswapv4-hook-attack"></a>

Cork Protocol suffered a $12M exploit caused by a combination of business-logic flaws and authorization weaknesses in its smart contracts.

1. Flawed Token Role Logic

Cork’s design allowed Depeg Swaps (DS) of one market to be improperly treated as the Redemption Asset (RA) in another market.

This meant that a token meant to hedge against a peg-loss could illegitimately function as backing collateral in a new, attacker-controlled market.

2. Rollover Pricing Exploit

The protocol’s rollover pricing relied on a historical implied yield average (HIYA) mechanism to set rates.

Under low-liquidity conditions, a single attacker trade could skew the pricing formula dramatically.

3. Missing Authorization in Hook Integration

Cork deployed a periphery contract that lacked the updated authorization safeguards.

As a result, attackers could call beforeSwap without proper permission checks.

This gave attacker the ability to split legitimate DS tokens into fake derivatives (“fake\_DS” and “fake\_CT”) and later redeem them for real DS

4. Combined Attack Path

By chaining the above weaknesses, the attacker executed a two-step exploit:

* Distort rollover pricing → acquire massive amounts of Cover Tokens essentially for free.
* Abuse the hook authorization flaw → redeem fake tokens into genuine assets, draining Cork’s liquidity vaults.
