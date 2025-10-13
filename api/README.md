---
description: Write queries, describe code scenarios and find matching contract code
icon: plug
---

# API



## How Glider represents the contract code

Before diving deep into the API classes and methods, let's see an example of how the Glider engine "understands" or represents the contract code.



Let's look at the [USDT token contract code](https://vscode.blockscan.com/ethereum/0xdac17f958d2ee523a2206206994597c13d831ec7):

```solidity
/*
...
*/

contract TetherToken is Pausable, StandardToken, BlackList {

    string public name;
    string public symbol;
    uint public decimals;
    address public upgradedAddress;
    bool public deprecated;

    //  The contract can be initialized with a number of tokens
    //  All the tokens are deposited to the owner address
    //
    // @param _balance Initial supply of the contract
    // @param _name Token Name
    // @param _symbol Token symbol
    // @param _decimals Token decimals
    function TetherToken(uint _initialSupply, string _name, string _symbol, uint _decimals) public {
        _totalSupply = _initialSupply;
        name = _name;
        symbol = _symbol;
        decimals = _decimals;
        balances[owner] = _initialSupply;
        deprecated = false;
    }

    // Forward ERC20 methods to upgraded contract if this one is deprecated
    function transfer(address _to, uint _value) public whenNotPaused {
        require(!isBlackListed[msg.sender]);
        if (deprecated) {
            return UpgradedStandardToken(upgradedAddress).transferByLegacy(msg.sender, _to, _value);
        } else {
            return super.transfer(_to, _value);
        }
    }

    // Forward ERC20 methods to upgraded contract if this one is deprecated
    function transferFrom(address _from, address _to, uint _value) public whenNotPaused {
        require(!isBlackListed[_from]);
        if (deprecated) {
            return UpgradedStandardToken(upgradedAddress).transferFromByLegacy(msg.sender, _from, _to, _value);
        } else {
            return super.transferFrom(_from, _to, _value);
        }
    }

    // Forward ERC20 methods to upgraded contract if this one is deprecated
    function balanceOf(address who) public constant returns (uint) {
        if (deprecated) {
            return UpgradedStandardToken(upgradedAddress).balanceOf(who);
        } else {
            return super.balanceOf(who);
        }
    }

    // Forward ERC20 methods to upgraded contract if this one is deprecated
    function approve(address _spender, uint _value) public onlyPayloadSize(2 * 32) {
        if (deprecated) {
            return UpgradedStandardToken(upgradedAddress).approveByLegacy(msg.sender, _spender, _value);
        } else {
            return super.approve(_spender, _value);
        }
    }

    // Forward ERC20 methods to upgraded contract if this one is deprecated
    function allowance(address _owner, address _spender) public constant returns (uint remaining) {
        if (deprecated) {
            return StandardToken(upgradedAddress).allowance(_owner, _spender);
        } else {
            return super.allowance(_owner, _spender);
        }
    }

    // deprecate current contract in favour of a new one
    function deprecate(address _upgradedAddress) public onlyOwner {
        deprecated = true;
        upgradedAddress = _upgradedAddress;
        Deprecate(_upgradedAddress);
    }

    // deprecate current contract if favour of a new one
    function totalSupply() public constant returns (uint) {
        if (deprecated) {
            return StandardToken(upgradedAddress).totalSupply();
        } else {
            return _totalSupply;
        }
    }

    // Issue a new amount of tokens
    // these tokens are deposited into the owner address
    //
    // @param _amount Number of tokens to be issued
    function issue(uint amount) public onlyOwner {
        require(_totalSupply + amount > _totalSupply);
        require(balances[owner] + amount > balances[owner]);

        balances[owner] += amount;
        _totalSupply += amount;
        Issue(amount);
    }

    // Redeem tokens.
    // These tokens are withdrawn from the owner address
    // if the balance must be enough to cover the redeem
    // or the call will fail.
    // @param _amount Number of tokens to be issued
    function redeem(uint amount) public onlyOwner {
        require(_totalSupply >= amount);
        require(balances[owner] >= amount);

        _totalSupply -= amount;
        balances[owner] -= amount;
        Redeem(amount);
    }

    function setParams(uint newBasisPoints, uint newMaxFee) public onlyOwner {
        // Ensure transparency by hardcoding limit beyond which fees can never be added
        require(newBasisPoints < 20);
        require(newMaxFee < 50);

        basisPointsRate = newBasisPoints;
        maximumFee = newMaxFee.mul(10**decimals);

        Params(basisPointsRate, maximumFee);
    }

    // Called when new token are issued
    event Issue(uint amount);

    // Called when tokens are redeemed
    event Redeem(uint amount);

    // Called when contract is deprecated
    event Deprecate(address newAddress);

    // Called if contract ever adds fees
    event Params(uint feeBasisPoints, uint maxFee);
}
```



For everything in the contract code (except comment sections), there is at least one entity that represents it in the Glider engine and allows the filtering and analysis of that data.

## Contracts

In Glider, every contract, interface, and library is represented by the [Contract](contract/) class.&#x20;

A set of contracts is represented by [Contracts](./#contracts) class.&#x20;

There are special flags and methods to distinguish or filter them.

In USDT the TetherToken will have a contract object for:

```solidity
contract TetherToken
```

Contract objects can be used to obtain full information about the contract, such as the deployed address, compiler versions/pragmas, state variables, base and derived contracts, etc.&#x20;

That said, the libraries, interfaces, and base contracts used in USDT code will also have a Contract object representing them:

```solidity
library SafeMath { // Contract (is_library: True)
//...
}
//...
contract Ownable { 
//...
}
//... 
```

As one address (one main contract) can have multiple interfaces, libraries, contracts declared or even derived, built in a complex folder structure, Glider will generate Contract objects for all of them, though the address will be the same, and only one contract will be considered to be the main.&#x20;

For the contract that is "main", meaning that its functions are being executed if a transaction is called, the engine marks this contract as "main" to distinguish it from others on the same address; see [Contract.is\_main()](contract/contract.is_main.md).

While the [Contract](contract/) class is used to obtain information about a single contract, the [Contracts](./#contracts) class is used to query and/or filter contracts from a set or the whole database.

Contracts contain references to other entities that belong to those contracts:

[Functions](callables/functions/)([Callables](callables/)), [Modifiers](callables/modifiers/)([Callables](callables/)), [StateVariables](statevariables/), [Structs](contract/contract.structs.md), [Enums](contract/contract.enums.md), [Errors](contract/contract.errors.md).

## Callables

Glider treats functions and modifiers as callable objects.&#x20;

Nonetheless, Glider has [Function](callable/function/) and [Modifier](callable/modifier/) classes that both derive from [Callable](callable/)

### Functions

Each function in the contract code is represented by a [Function](callable/function/) object.

The set of functions is represented by the [Functions](./#functions) object.

E.g transfer function in the TetherToken contract

```solidity
    // Forward ERC20 methods to upgraded contract if this one is deprecated
    function transfer(address _to, uint _value) public whenNotPaused {
        require(!isBlackListed[msg.sender]);
        if (deprecated) {
            return UpgradedStandardToken(upgradedAddress).transferByLegacy(msg.sender, _to, _value);
        } else {
            return super.transfer(_to, _value);
        }
    }
```

Or any other function, for example `mul, div, sub, add` functions in the SafeMath library:

```solidity
library SafeMath {
    function mul(uint256 a, uint256 b) internal pure returns (uint256) {
        if (a == 0) {
            return 0;
        }
        uint256 c = a * b;
        assert(c / a == b);
        return c;
    }

    function div(uint256 a, uint256 b) internal pure returns (uint256) {
        // assert(b > 0); // Solidity automatically throws when dividing by 0
        uint256 c = a / b;
        // assert(a == b * c + a % b); // There is no case in which this doesn't hold
        return c;
    }

    function sub(uint256 a, uint256 b) internal pure returns (uint256) {
        assert(b <= a);
        return a - b;
    }

    function add(uint256 a, uint256 b) internal pure returns (uint256) {
        uint256 c = a + b;
        assert(c >= a);
        return c;
    }
}
```

### Modifiers

Each modifier is represented by a [Modifier](callable/modifier/) object.

The set of modifiers is represented by a [Modifiers](./#modifiers) object.

E.g the `onlyOwner` modifier in `Ownable` contract:

```solidity
    modifier onlyOwner() {
        require(msg.sender == owner);
        _;
    }
```

Or `onlyPayloadSize` in `BasicToken` contract:

```solidity
    modifier onlyPayloadSize(uint size) {
        require(!(msg.data.length < size + 4));
        _;
    }
```

And `whenNotPaused` and `whenPaused` modifiers in Pauable:

```solidity
  modifier whenNotPaused() {
    require(!paused);
    _;
  }

  /**
   * @dev Modifier to make a function callable only when the contract is paused.
   */
  modifier whenPaused() {
    require(paused);
    _;
  }

```

[Function](callable/function/) and [Modifier](callable/modifier/) objects can be used to obtain data about a specific object, while [Functions](./#functions) and [Modifiers](./#modifiers) objects are used to query and/or filter functions/modifiers by specific properties from a set or the whole database.

Functions have references to the modifiers that are being used in the function and vice versa.

{% hint style="info" %}
See methods: [Modifier.functions()](callable/modifier/modifier.functions.md) and [Function.modifiers()](callable/function/function.modifiers.md) for a single function/modifier instance

Also: [Modifiers.functions()](callable/modifier/modifier.functions.md) and [Functions.modifiers()](callable/function/function.modifiers.md) for the set
{% endhint %}

One of the most important references that functions/modifiers have is their reference to their [instructions](instructions/).

## Instructions

An easy way to think of an instruction is anything that ends with a semicolon ';' in the code. However, this is not always the case, as with some instructions like if-statements, don't use semicolons.

E.g in the function transfer:

```solidity
    function transfer(address _to, uint _value) public whenNotPaused {
        require(!isBlackListed[msg.sender]);
        if (deprecated) {
            return UpgradedStandardToken(upgradedAddress).transferByLegacy(msg.sender, _to, _value);
        } else {
            return super.transfer(_to, _value);
        }
    }
```

The instructions will be:

```solidity
require(!isBlackListed[msg.sender]);
--
if (deprecated)
--
return UpgradedStandardToken(upgradedAddress).transferByLegacy(msg.sender, _to, _value);
--
else
--
return super.transfer(_to, _value);
```

As the Modifier is also a [Callable](callable/), it also has instructions:

```solidity
  modifier whenNotPaused() {
    require(!paused);
    _;
  }
```

Here the `whenNotPaused` modifier's instructions will be:

```solidity
require(!paused);
--
_;
```

{% hint style="info" %}
Note that the special underline symbol (\_), which is also called placer/placeholder, is also considered an instruction.

See methods: [Instruction.is\_placer()](instruction/instruction.is_placeholder.md), [Modifier.placer\_instructions()](modifier/modifier.placeholder_instructions.md), [Modifiers.placer\_instructions()](modifiers/modifiers.placeholder_instructions.md)
{% endhint %}

The constructors are also considered functions; special methods can be used to query and check that a function is a constructor.

As with other entities, the [Instruction](instruction/) object is used to obtain data and analyze one specific instruction, and the [Instructions](./#instructions) object is used to query/filter instructions in a set or in a whole database.

An instruction on its own usually consists of different parts, for example:

```solidity
require(!paused);
```

This instruction consists of a `require()` call, a boolean expression `!paused`

In Glider, the "parts" of the instruction are called [values](value/).

### Value

The Value object represents a "part" of the instruction. Value by itself is a base class for different types of values such as [Call](value/call/), [Var](broken-reference), [Literal](value/literal/) etc.

E.g. in the instruction

```solidity
require(paused);
        <-Var->
<----Call----->
```

The "part" representing the require call, will be of type [Call](value/call/) (class derived from Value), and the value `paused` will be of type [Var](broken-reference) (class derived from Value) as it represents a variable.

## Arguments

The Argument and Arguments object are mainly used in context of functions and modifiers (as they are the ones having arguments).

E.g for the function `setParams` in TetherToken:

```solidity
function setParams(uint newBasisPoints, uint newMaxFee) public onlyOwner {
//...
}
```

The `newBasisPoints` and `newMaxFee` are arguments of the function, and an Argument object will be used to represent each of them.

The [Argument](argument/) class is used to represent a single argument of the function/modifier (callable), while the [Arguments](./#arguments) class is used to represent a set of arguments.

## StateVariables

The contracts also have state (storage) variables defined; Glider allows the users to query, filter and analyze them as well.&#x20;

E.g in the contract TetherToken:

```solidity
    string public name;
    string public symbol;
    uint public decimals;
    address public upgradedAddress;
    bool public deprecated;
```

or in BasicToken:

```solidity
    mapping(address => uint) public balances;

    // additional variables for use if transaction fees ever became necessary
    uint public basisPointsRate = 0;
    uint public maximumFee = 0;
```

These state variables will be represented by a StateVariable object each or a StateVariables object for a set (or whole database).

## LocalVariables

The local variables of functions/modifiers are represented by [LocalVariable](localvariable/) and [LocalVariables](./#localvariables) classes.

E.g. in `BasicToken.transfer()` function:

```solidity
    function transfer(address _to, uint _value) public onlyPayloadSize(2 * 32) {
        uint fee = (_value.mul(basisPointsRate)).div(10000);
        if (fee > maximumFee) {
            fee = maximumFee;
        }
        uint sendAmount = _value.sub(fee);
        balances[msg.sender] = balances[msg.sender].sub(_value);
        balances[_to] = balances[_to].add(sendAmount);
        if (fee > 0) {
            balances[owner] = balances[owner].add(fee);
            Transfer(msg.sender, owner, fee);
        }
        Transfer(msg.sender, _to, sendAmount);
    }
```

The `uint fee` and `uint sendAmount` will be the local variables defined in the function.
