---
description: Adds a filter to get functions/modifiers having specified callee names.
---

# Callables.with\_callee\_names()

`with_callee_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables that have all of the specified callees (functions that are being called within a function/modifier). Returns a filtered [Callables](./) child object.&#x20;

This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

## Function Example

```python
from glider import *

def query():
  # Retrieve all the modifiers with the signature `nonReentrant()`
  functions = Functions().with_callee_names(["owner", "msgSender"]).exec(1)

  # Return the first five modifiers
  return functions
```

## Output

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Token"
"sol_function":solidity
constructor () {
        uniswapV2Pair = IUniswapV2Factory(uniswapV2Router.factory()).createPair(address(this), uniswapV2Router.WETH());
        _taxWallet = payable(_msgSender());
        _balances[_msgSender()] = _tTotal;
        _isExcludedFromFee[owner()] = true;
        _isExcludedFromFee[address(this)] = true;
        _isExcludedFromFee[_taxWallet] = true;
        _isExcludedFromFee[address(uniswapV2Router)] = true;
        _approve(msg.sender, address(this), type(uint256).max);
        _approve(address(this), address(uniswapV2Router), type(uint256).max);
        emit Transfer(address(0), _msgSender(), _tTotal);
    }
}
```

## Modifier Example

```python
from glider import *

def query():
  # Retrieve all the modifiers with the signature `nonReentrant()`
  modifiers = Modifiers().with_callee_names(["owner", "msgSender"]).exec(1)

  # Return the first five modifiers
  return modifiers
```

## Output

```solidity
"root":{3 items
"contract":string"0x5e6b2027f794a069bfa5e80195e22544d40ae600"
"contract_name":string"Ownable"
"sol_modifier":solidity
modifier onlyOwner() {
        require(owner() == _msgSender(), "Ownable: caller is not the owner");
        _;
    }
```



