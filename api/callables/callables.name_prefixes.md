# Callables.name\_prefixes()

Adds a filter to get callables whose names have prefixes from the given list of prefixes. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a single prefix, refer to [Callables.name\_prefix()](callables.name\_prefix.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `min` or `max` as prefix
  functions = Functions().name_prefixes(["min", "max"]).exec(100)

  # Return the first five functions
  return functions[0:5]
```

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP",
        "sol_function": "function mint() external onlyMinterOrOwner returns (uint256) {\n        _mint(address(this),nextId);\n        flowRates[nextId] = _testFlowRate;\n\n        uint256 ltpId = nextId;\n        nextId += 1;\n        return ltpId;\n    }"
    },
    {
        "contract": "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D",
        "contract_name": "IPoolTokens",
        "sol_function": "function mint(MintParams calldata params,address to) external returns (uint256);"
    },
    {
        "contract": "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D",
        "contract_name": "PoolTokens",
        "sol_function": "function mint(MintParams calldata params,address to)\n    external\n    override\n    returns (uint256 tokenId)\n  {\n    return self_mint(params,to,lastTokenId + 1);\n  }"
    },
    {
        "contract": "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D",
        "contract_name": "ICreditLine",
        "sol_function": "function maxLimit() external view returns (uint256);"
    },
    {
        "contract": "0x27A05e7a40F2d980F8853e94c3cE54C70e68527D",
        "contract_name": "IV2CreditLine",
        "sol_function": "function maxLimit() external view returns (uint256);"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `before` or `after` as prefix
  modifiers = Modifiers().name_prefixes(["before", "after"]).exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x2a14381a8C42C36782819aafB5328CAeE8BD5905",
        "contract_name": "FYToken",
        "sol_modifier": "modifier afterMaturity() {\n        require(\n            uint32(block.timestamp) >= maturity,\"Only after maturity\"\n        );\n        _;\n    }"
    },
    {
        "contract": "0x2a14381a8C42C36782819aafB5328CAeE8BD5905",
        "contract_name": "FYToken",
        "sol_modifier": "modifier beforeMaturity() {\n        require(\n            uint32(block.timestamp) < maturity,\"Only before maturity\"\n        );\n        _;\n    }"
    },
    {
        "contract": "0xeD7d6b515e4f4D523bc80E0A220301197FF27c96",
        "contract_name": "FYToken",
        "sol_modifier": "modifier afterMaturity() {\n        require(\n            uint32(block.timestamp) >= maturity,\"Only after maturity\"\n        );\n        _;\n    }"
    },
    {
        "contract": "0xeD7d6b515e4f4D523bc80E0A220301197FF27c96",
        "contract_name": "FYToken",
        "sol_modifier": "modifier beforeMaturity() {\n        require(\n            uint32(block.timestamp) < maturity,\"Only before maturity\"\n        );\n        _;\n    }"
    },
    {
        "contract": "0xB79e217DE1FB65a5bC5DbDDB0C63eF61F4cc2F1E",
        "contract_name": "FYToken",
        "sol_modifier": "modifier afterMaturity() {\n        require(\n            uint32(block.timestamp) >= maturity,\"Only after maturity\"\n        );\n        _;\n    }"
    }
]
```
