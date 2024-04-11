# Callables.name\_prefix()

Adds a filter to get callables whose names have the given prefix. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a list of prefixes, refer to [Callables.name\_prefixes()](callables.name\_prefixes.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `min` as prefix
  functions = Functions().name_prefix("min").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

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
        "contract": "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
        "contract_name": "IConfigProvider",
        "sol_function": "function minVotingPeriod() external view returns (uint256);"
    },
    {
        "contract": "0x400a7e0960b63d3288591ee0e6B6D9578eAFFe23",
        "contract_name": "ISTABLEX",
        "sol_function": "function mint(address account,uint256 amount) external;"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `only` as prefix
  modifiers = Modifiers().name_prefix("only").exec(100)

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
