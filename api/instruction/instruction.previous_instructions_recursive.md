---
description: >-
  Returns the set of all instructions preceding the current node in the control
  flow graph.
---

# Instruction.previous\_instructions\_recursive()

`previous_instructions_recursive() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](./)`]`

The function returns all instructions that are previous to the instruction in the CFG (control flow graph).

The difference between the extended\_previous\_instructions() function and [previous\_instructions()](instruction.previous_instructions.md) is that the former works in an inter-procedural manner.

_The function is inter-procedural, and follows function calls; for the **intra**-procedural variant of this function, use_ [_previous\_instructions()_](instruction.previous_instructions.md)_._



For example, in the function:

```solidity
function mul(uint256 a, uint256 b) internal pure returns (uint256) {
        if (a == 0) {
            return 0;
        }
        uint256 c = a * b;
        require(c / a == b, "SafeMath: multiplication overflow");
        return c;
    }
```

for the instruction:

```solidity
require(c / a == b, "SafeMath: multiplication overflow")
```

having that the mul() is being called inside the function:

```solidity
function _transfer(address from, address to, uint256 amount) private {
        uint256 taxAmount=0;
        if (!_isExcludedFromFee[from] && !_isExcludedFromFee[to]) {
            require(tradeOpen, "Trading not open");
            taxAmount = amount.mul((_buyCount>_reduceBuyTaxAt)?_finalBuyTax:_initialBuyTax).div(100);

            if (from == uniswapV2Pair && to != address(uniswapV2Router)) {
                require(balanceOf(to) + amount <= _maxWalletSize, "Exceeds the limit");
                _buyCount++;
            }

            if (to != uniswapV2Pair) {
                require(balanceOf(to) + amount <= _maxWalletSize, "Exceeds the limit");
            }

            if(to == uniswapV2Pair && from!= address(this) ){
                taxAmount = amount.mul((_buyCount>_reduceSellTaxAt)?_finalSellTax:_initialSellTax).div(100);
            }

        //....
    }
```

the function will return previous instructions from mul():

```solidity
       if (a == 0) {
            return 0;
        }
        uint256 c = a * b;
```

as well as from \_transfer():

```solidity
        uint256 taxAmount=0;
        if (!_isExcludedFromFee[from] && !_isExcludedFromFee[to]) {
            require(tradeOpen, "Trading not open");
            taxAmount = amount.mul((_buyCount>_reduceBuyTaxAt)?_finalBuyTax:_initialBuyTax).div(100);

            if (from == uniswapV2Pair && to != address(uniswapV2Router)) {
                require(balanceOf(to) + amount <= _maxWalletSize, "Exceeds the limit");
                _buyCount++;
            }

            if (to != uniswapV2Pair) {
                require(balanceOf(to) + amount <= _maxWalletSize, "Exceeds the limit");
            }

            if(to == uniswapV2Pair && from!= address(this) ){
                taxAmount = amount.mul((_buyCount>_reduceSellTaxAt)?_finalSellTax:_initialSellTax).div(100);
            }
```

Furthermore, it will also return instructions from transferFrom() function as the \_transfer() is being called from there as well:

```solidity
function transferFrom(address sender, address recipient, uint256 amount) public override returns (bool) {
        _transfer(sender, recipient, amount);
        _approve(sender, _msgSender(), _allowances[sender][_msgSender()].sub(amount, "ERC20: transfer amount exceeds allowance"));
        return true;
    }
```

## Query Example

```python
from glider import *


def query():
  instructions = Functions().with_all_properties([MethodProp.INTERNAL]).instructions().with_callee_name('require').exec(1, 2)

  return instructions + list(instructions[0].previous_instructions_recursive())
```

## Example Output

<figure><img src="../../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
