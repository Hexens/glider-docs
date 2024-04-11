# Callables.with\_arg\_memory\_type()

Adds a filter to get callables having specified argument memory type. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have a storage argument
  functions = Functions().with_arg_memory_type("storage").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "EnumerableSet",
        "sol_function": "function _add(Set storage set,bytes32 value) private returns (bool) {\n        if (!_contains(set,value)) {\n            set._values.push(value);\n            \n            \n            set._indexes[value] = set._values.length;\n            return true;\n        } else {\n            return false;\n        }\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "EnumerableSet",
        "sol_function": "function _remove(Set storage set,bytes32 value) private returns (bool) {\n        \n        uint256 valueIndex = set._indexes[value];\n\n        if (valueIndex != 0) { \n            \n            \n            \n\n            uint256 toDeleteIndex = valueIndex - 1;\n            uint256 lastIndex = set._values.length - 1;\n\n            \n            \n\n            bytes32 lastvalue = set._values[lastIndex];\n\n            \n            set._values[toDeleteIndex] = lastvalue;\n            \n            set._indexes[lastvalue] = toDeleteIndex + 1; \n\n            \n            set._values.pop();\n\n            \n            delete set._indexes[value];\n\n            return true;\n        } else {\n            return false;\n        }\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "EnumerableSet",
        "sol_function": "function _contains(Set storage set,bytes32 value) private view returns (bool) {\n        return set._indexes[value] != 0;\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "EnumerableSet",
        "sol_function": "function _length(Set storage set) private view returns (uint256) {\n        return set._values.length;\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "EnumerableSet",
        "sol_function": "function _at(Set storage set,uint256 index) private view returns (bytes32) {\n        require(set._values.length > index,\"EnumerableSet: index out of bounds\");\n        return set._values[index];\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have a calldata argument
  modifiers = Modifiers().with_arg_memory_type("calldata").exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x78C96ABf20bf43E129FF27B25a135c0E70ceb2bc",
        "contract_name": "ChargedParticles",
        "sol_modifier": "modifier managerEnabled(string calldata walletManagerId) {\n    require(_chargedManagers.isWalletManagerEnabled(walletManagerId),\"CP:E-419\");\n    _;\n  }"
    },
    {
        "contract": "0x78C96ABf20bf43E129FF27B25a135c0E70ceb2bc",
        "contract_name": "ChargedParticles",
        "sol_modifier": "modifier basketEnabled(string calldata basketManagerId) {\n    require(_chargedManagers.isNftBasketEnabled(basketManagerId),\"CP:E-419\");\n    _;\n  }"
    },
    {
        "contract": "0xd2836c88674020003446e5f225addcf3225c56d0",
        "contract_name": "Arbitrator",
        "sol_modifier": "modifier requireArbitrationFee(bytes calldata _extraData) {\n        require(msg.value >= arbitrationCost(_extraData),\"Not enough ETH to cover arbitration costs.\");\n        _;\n    }"
    },
    {
        "contract": "0xd2836c88674020003446e5f225addcf3225c56d0",
        "contract_name": "Arbitrator",
        "sol_modifier": "modifier requireAppealFee(uint _disputeID,bytes calldata _extraData) {\n        require(msg.value >= appealCost(_disputeID,_extraData),\"Not enough ETH to cover appeal costs.\");\n        _;\n    }"
    },
    {
        "contract": "0x07ac2e0fa5944c81f66dc54d3d54d58f04bb5d10",
        "contract_name": "KCGStaking",
        "sol_modifier": "modifier checkArgsLength(uint256[] calldata tokenIds,uint256[] calldata timeframe) {\n        require(tokenIds.length == timeframe.length,\"token ids and time frame must be same length\");\n        _;\n    }"
    }
]
```
