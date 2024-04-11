# Callables.with\_signatures()

Adds a filter to get callables that have any of the given signatures. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a single signature, refer to [Callables.with\_signature()](callables.with\_signature.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions that have `approve(address)` or `claim(address,uint256)` as signatures
  functions = Functions() \
      .with_signatures([
          "approve(address)",
          "claim(address,uint256)"
      ]) \
      .exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0xb0d5eAC91C77997647875B9A72d5Bff1e78DAa78",
        "contract_name": "Arb",
        "sol_function": "function approve(address bamm) external {\n        ERC20Like(LUSD).approve(address(bamm),uint(-1));\n    }"
    },
    {
        "contract": "0xea883c61b9eafd13ce094a66da3b379619133e7f",
        "contract_name": "DSTokenAbstract",
        "sol_function": "function approve(address) external returns (bool);"
    },
    {
        "contract": "0xa64ef2edf816072f90afc89b21aae883d5a4de00",
        "contract_name": "DSToken",
        "sol_function": "function approve(address guy) public stoppable returns (bool) {\n        return super.approve(guy,uint(-1));\n    }"
    },
    {
        "contract": "0x1c45e40a948bB9B4684B94239d5FD73e3a9cAD8A",
        "contract_name": "IRegistry",
        "sol_function": "function approve(address _addr) external;"
    },
    {
        "contract": "0x1c45e40a948bB9B4684B94239d5FD73e3a9cAD8A",
        "contract_name": "Registry",
        "sol_function": "function approve(address _addr) external override onlyOwner {\n        require(!_approved[_addr],\"_addr approved\");\n        _approved[_addr] = true;\n        emit Approve(_addr);\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve all the modifiers that have `nonReentrant()` or `initializer()` as their signatures
  modifiers = Modifiers() \
    .with_signatures([
      "nonReentrant()",
      "initializer()"
    ]) \
    .exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
        "contract_name": "Initializable",
        "sol_modifier": "modifier initializer() {\n        require(_initializing || _isConstructor() || !_initialized,\"Initializable: contract is already initialized\");\n\n        bool isTopLevelCall = !_initializing;\n        if (isTopLevelCall) {\n            _initializing = true;\n            _initialized = true;\n        }\n\n        _;\n\n        if (isTopLevelCall) {\n            _initializing = false;\n        }\n    }"
    },
    {
        "contract": "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
        "contract_name": "ChainlinkInceptionPriceFeed",
        "sol_modifier": "modifier initializer() {\n        require(_initializing || _isConstructor() || !_initialized,\"Initializable: contract is already initialized\");\n\n        bool isTopLevelCall = !_initializing;\n        if (isTopLevelCall) {\n            _initializing = true;\n            _initialized = true;\n        }\n\n        _;\n\n        if (isTopLevelCall) {\n            _initializing = false;\n        }\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "Initializable",
        "sol_modifier": "modifier initializer() {\n        require(_initializing || _isConstructor() || !_initialized,\"Initializable: contract is already initialized\");\n\n        bool isTopLevelCall = !_initializing;\n        if (isTopLevelCall) {\n            _initializing = true;\n            _initialized = true;\n        }\n\n        _;\n\n        if (isTopLevelCall) {\n            _initializing = false;\n        }\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "Core",
        "sol_modifier": "modifier initializer() {\n        require(_initializing || _isConstructor() || !_initialized,\"Initializable: contract is already initialized\");\n\n        bool isTopLevelCall = !_initializing;\n        if (isTopLevelCall) {\n            _initializing = true;\n            _initialized = true;\n        }\n\n        _;\n\n        if (isTopLevelCall) {\n            _initializing = false;\n        }\n    }"
    },
    {
        "contract": "0xb51Da721B77Db063B02b79D7e79558b9C2e34Ea6",
        "contract_name": "Initializable",
        "sol_modifier": "modifier initializer() {\n    require(initializing || isConstructor() || !initialized,\"Contract instance has already been initialized\");\n\n    bool isTopLevelCall = !initializing;\n    if (isTopLevelCall) {\n      initializing = true;\n      initialized = true;\n    }\n\n    _;\n\n    if (isTopLevelCall) {\n      initializing = false;\n    }\n  }"
    }
]
```
