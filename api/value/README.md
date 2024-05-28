# Value

This class represents different parts of an [instruction](../instruction/).

While an easy way to understand what instruction is is to imagine that it is everything that ends with ";" e.g

```solidity
require(predicate); 
uint a = 0;
foo(bar()-1);
```

These are all examples of instructions.

Value represents the internal parts of instruction, e.g for the instruction:

```solidity
foo(bar()-1);
```

the `bar()` - call, `bar()-1` expression and `foo(bar()-1)` calls will be the values of the instruction.

While the Value is a very important part of the engine, one will most likely never work with the Value class directly, but rather with the derived classes of the Value, which are:

* [Call](call/)
* [Var](var/)
* [ValueExpression](valueexpression/)
* ValueContractType
* [Literal](literal/)

