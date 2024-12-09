---
description: >-
  Returns the set of all instructions following the current node in the control
  flow graph.
---

# Instruction.extended\_next\_instructions()

`extended_next_instructions() →` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](./)`]`

The difference between the extended\_next\_instructions() function and [next\_instructions()](instruction.next_instructions.md) is that this function works in an **inter**-procedural manner and returns all instructions following the current instruction in the CFG (control-flow-graph).

_The function is intra-procedural, and follows function calls; for the **intra**-procedural variant of this function, use_ [_next\_instructions()_](instruction.next_instructions.md)_._



For example, in the function:

```solidity
function transferFrom(
        address sender,
        address recipient,
        uint256 amount
    ) public virtual override returns (bool) {
        _transfer(sender, recipient, amount);

        uint256 currentAllowance = _allowances[sender][_msgSender()];
        require(currentAllowance >= amount, "ERC20: transfer amount exceeds allowance");
        unchecked {
            _approve(sender, _msgSender(), currentAllowance - amount);
        }

        return true;
    }
```

for the instruction:

```solidity
require(currentAllowance >= amount, "ERC20: transfer amount exceeds allowance")
```

the function will return instructions from `transferFrom()`, as well as from `_approve()` and `_msgSender()`.&#x20;

### Query Example

```python
from glider import *
def query():
  instructions = Functions().with_all_properties([MethodProp.INTERNAL]).instructions().with_callee_function_name('require').exec(1,2)

  return instructions + list(instructions[0].extended_previous_instructions())
```

### Output Example

```solidity
"root":{4 items
"contract":string"0x5e6b2027f794a069bfa5e80195e22544d40ae600"
"contract_name":string"NATEHALLINAN"
"sol_function":solidity
function transferFrom(
        address sender,
        address recipient,
        uint256 amount
    ) public virtual override returns (bool) {
        _transfer(sender, recipient, amount);

        uint256 currentAllowance = _allowances[sender][_msgSender()];
        require(currentAllowance >= amount, "ERC20: transfer amount exceeds allowance");
        unchecked {
            _approve(sender, _msgSender(), currentAllowance - amount);
        }

        return true;
    }
"sol_instruction":solidity
require(currentAllowance >= amount, "ERC20: transfer amount exceeds allowance")
},
...
"root":{4 items
"contract":string"0x5e6b2027f794a069bfa5e80195e22544d40ae600"
"contract_name":string"NATEHALLINAN"
"sol_function":solidity
function _approve(
        address owner,
        address spender,
        uint256 amount
    ) internal virtual {
        require(owner != address(0), "ERC20: approve from the zero address");
        require(spender != address(0), "ERC20: approve to the zero address");

        _allowances[owner][spender] = amount;
        emit Approval(owner, spender, amount);
    }
"sol_instruction":solidity
require(spender != address(0), "ERC20: approve to the zero address")
},
...
"root":{4 items
"contract":string"0x5e6b2027f794a069bfa5e80195e22544d40ae600"
"contract_name":string"NATEHALLINAN"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
"sol_instruction":solidity
{
        return msg.sender;
    }
}
...
```



{% hint style="info" %}
The function returns APISet, instead of APIList, in case the result of the function is used as the return value of the query it must be casted to `list()`
{% endhint %}
