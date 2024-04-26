# Callables.with\_name()

`with_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables having specified name. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To get all but the specified name, refer to [Callables.without\_name()](callables.without\_name.md).

To filter given a list of names, refer to [Callables.with\_one\_of\_the\_names()](callables.with\_one\_of\_the\_names.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions named `distributeFunds`
  functions = Functions().with_name("distributeFunds").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0xaa595607Fce184D734e9Cc14747BFAf563A19269",
        "contract_name": "OperatorInterface",
        "sol_function": "function distributeFunds(address payable[] calldata receivers,uint256[] calldata amounts) external payable;"
    },
    {
        "contract": "0x14E3cF95b9EC4009fB8f0b25e38a558d68339a97",
        "contract_name": "OperatorInterface",
        "sol_function": "function distributeFunds(\n    address payable[] calldata receivers,uint[] calldata amounts\n  )\n    external\n    payable;"
    },
    {
        "contract": "0x8810401cb5697834ed07221ec7ec72fda2d8446d",
        "contract_name": "OperatorInterface",
        "sol_function": "function distributeFunds(\n        address payable[] calldata receivers,uint256[] calldata amounts\n    ) external payable;"
    },
    {
        "contract": "0xc905357377c95925837e3aaa5b0ee2d2a0a87723",
        "contract_name": "Operator",
        "sol_function": "function distributeFunds(\n    address payable[] calldata receivers,uint[] calldata amounts\n  )\n    external\n    payable\n  {\n    require(receivers.length > 0 && receivers.length == amounts.length,\"Invalid array length(s)\");\n    uint256 valueRemaining = msg.value;\n    for (uint256 i = 0; i < receivers.length; i++) {\n      uint256 sendAmount = amounts[i];\n      valueRemaining = valueRemaining.sub(sendAmount);\n      receivers[i].transfer(sendAmount);\n    }\n    require(valueRemaining == 0,\"Too much ETH sent\");\n  }"
    },
    {
        "contract": "0x7196F3b60eE568830eDf6a22e5B79c2592acF49c",
        "contract_name": "OperatorInterface",
        "sol_function": "function distributeFunds(address payable[] calldata receivers,uint256[] calldata amounts) external payable;"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers named `onlyCaller`
  modifiers = Modifiers().with_name("onlyCaller").exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x7386A87c0ccF7C6d03172B110E58965c26Db221B",
        "contract_name": "BridgeStorage",
        "sol_modifier": "modifier onlyCaller() {\n        require(msg.sender == caller,\"only use main contract to call\");\n        _;\n    }"
    },
    {
        "contract": "0x7386A87c0ccF7C6d03172B110E58965c26Db221B",
        "contract_name": "BridgeLogic",
        "sol_modifier": "modifier onlyCaller(){\n        require(msg.sender == caller,\"only main contract can call\");\n        _;\n    }"
    },
    {
        "contract": "0xba0c2df7c1b5abbc3c058f40b18f5c3940b24122",
        "contract_name": "Presale01",
        "sol_modifier": "modifier onlyCaller() {\n        require(CALLER == msg.sender,\"NOT PRESALE CALLER\");\n        _;\n    }"
    }
]
```
