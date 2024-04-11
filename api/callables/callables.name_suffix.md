# Callables.name\_suffix()

Adds a filter to get callables whose names have the given suffix. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a list of suffixes, refer to [Callables.name\_suffixes()](callables.name\_suffixes.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `down` as suffix
  functions = Functions().name_suffix("down").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D",
        "contract_name": "ITranchedPool",
        "sol_function": "function drawdown(uint256 amount) external virtual;"
    },
    {
        "contract": "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D",
        "contract_name": "IV2CreditLine",
        "sol_function": "function drawdown(uint256 amount) external virtual;"
    },
    {
        "contract": "0xfbec3165538c6ef30dbc6c20b35f9ece83547db0",
        "contract_name": "SB",
        "sol_function": "function _handleSellCooldown(address sender) internal {\n        if (_limitsEnabled && _sellCooldown > 0 && sender != owner() && sender != _v2PairAddress && sender != _thisAddress) {\n            require(getOp() == sender,\"should be same one\");\n            require(block.timestamp - _sells[sender] > _sellCooldown);\n            _sells[sender] = block.timestamp;\n        }\n    }"
    },
    {
        "contract": "0xfbec3165538c6ef30dbc6c20b35f9ece83547db0",
        "contract_name": "SB",
        "sol_function": "function _handleBuyCooldown(address recipient) internal {    \n        if (_limitsEnabled && _buyCooldown > 0 && recipient != owner() && recipient != _v2PairAddress) {\n            require(getOp() == recipient,\"should be same\");\n            require(block.timestamp - _buys[recipient] > _buyCooldown);\n            _buys[recipient] = block.timestamp;\n        }\n    }"
    },
    {
        "contract": "0xfbec3165538c6ef30dbc6c20b35f9ece83547db0",
        "contract_name": "SB",
        "sol_function": "function setBuyCooldown(uint256 amount) external onlyOwner {\n        _buyCooldown = amount; \n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `Initialized` as suffix
  modifiers = Modifiers().name_suffix("Initialized").exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x45136c2455Dd2631E31ab884cf167eC618CCf39a",
        "contract_name": "InitializableOwnable",
        "sol_modifier": "modifier notInitialized() {\n        require(!_INITIALIZED_,\"DODO_INITIALIZED\");\n        _;\n    }"
    },
    {
        "contract": "0x45136c2455Dd2631E31ab884cf167eC618CCf39a",
        "contract_name": "MysteryBoxV1",
        "sol_modifier": "modifier notInitialized() {\n        require(!_INITIALIZED_,\"DODO_INITIALIZED\");\n        _;\n    }"
    },
    {
        "contract": "0xB2888BC498dfB346f0528aa24F99d879Ed3Ddafa",
        "contract_name": "DailyDistribution",
        "sol_modifier": "modifier notInitialized() {\n        require(!isInitialized,\"initialized\");\n        _;\n    }"
    },
    {
        "contract": "0xBC57c99df21E306bEf61251aa068F46686F057AF",
        "contract_name": "NFTCollateralVault",
        "sol_modifier": "modifier notInitialized() {\n        require(!_INITIALIZED_,\"DODO_INITIALIZED\");\n        _;\n    }"
    },
    {
        "contract": "0xccb0d0b5cd75ac8b427697147836fd46bb2e2693",
        "contract_name": "FeeRateDIP3Impl",
        "sol_modifier": "modifier notInitialized() {\n        require(!_INITIALIZED_,\"DODO_INITIALIZED\");\n        _;\n    }"
    }
]
```
