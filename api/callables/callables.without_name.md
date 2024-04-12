# Callables.without\_name()

`without_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables that don't have the specified name. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To get the callables with a specified name, refer to [Callables.with\_name()](callables.with\_name.md).

To filter given a list of undesired names, refer to [Callables.without\_names()](callables.without\_names.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions that are not named `distributeFunds`
  functions = Functions().without_name("distributeFunds").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Context",
        "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Context",
        "sol_function": "function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_function": "function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_function": "constructor() {\n        _setOwner(_msgSender());\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that are not named `onlyCaller`
  modifiers = Modifiers().without_name("onlyCaller").exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_modifier": "modifier onlyOwner() {\n        require(owner() == _msgSender(),\"Ownable: caller is not the owner\");\n        _;\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP",
        "sol_modifier": "modifier onlyOwner() {\n        require(owner() == _msgSender(),\"Ownable: caller is not the owner\");\n        _;\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP",
        "sol_modifier": "modifier onlyMinter() {\n        require(msg.sender == minter,'Sender is not the minter');\n        _;\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP",
        "sol_modifier": "modifier onlyMinterOrOwner() {\n        require( (msg.sender == minter) || (msg.sender == owner()),'Sender is not the minter nor owner');\n        _;\n    }"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "Owned",
        "sol_modifier": "modifier onlyOwner {\n        _onlyOwner();\n        _;\n    }"
    }
]
```
