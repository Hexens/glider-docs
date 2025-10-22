---
icon: person-falling
cover: ../.gitbook/assets/Glider QDB (1).png
coverY: 0
layout:
  width: default
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Common pitfalls of Glider

Some issues are currently impossible or unviable to formalize as a query. To provide general guidance on what most likely will not work, here are two main points.

* Any query that requires reading from the state will not work, as Glider currently doesn't support reading state data from the chain. For example, consider the first issue in the Medium section:\
  &#xNAN;_**Swap calls to various DeFi apps with slippage hardcoded to 0.**_\
  There may be cases where the slippage is stored in a storage variable. In such cases, we cannot query for that value because we wouldn't be able to check whether the slippage storage variable is set to 0. Therefore, we must query for hardcoded 0s in the contract instead.
* It is largely unviable to try and find a function with specific functionality you have in mind, as it is nearly impossible to account for all edge cases. You will either have too high a false positive rate, or your query will be too computationally intensive and hit Glider's limits. For example, suppose you want to find all possible iterations of the ERC4626 deposit function without searching by function name or signature. You might think you can query for a function that takes one token from the user, gives another token back, and increments some variable. However, this query would also return many DEX contracts where the user gives a token, an internal balance counter is incremented, and the user receives another token. If you start accounting for every possible edge case (which, in our experience, is mostly impossible), you will start hitting Glider limits. That said, if you believe you can find a significant bug without being too computationally heavy, we would be more than happy to receive your query and as such don't feel discouraged from trying. Even in the worst-case scenario where your query doesn't work, you will learn a lot about Glider.

