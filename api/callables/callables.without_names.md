# Callables.without\_names()

`without_names(`_`names: List[str]`_`,`` `_`sensitivity: bool = True`_`) →` [`Callables`](./)

Adds a filter to get callables that that don't have the specified names. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To get the callables without a specified name, refer to [Callables.without\_name()](callables.without\_name.md).

To filter given a list of names, refer to [Callables.with\_one\_of\_the\_names()](callables.with\_one\_of\_the\_names.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions that are not named `_msgSender` and `_msgData`
  functions = Functions().without_names(["_msgSender", "_msgData"]).exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_function": "constructor() {\n        _setOwner(_msgSender());\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_function": "function owner() public view virtual returns (address) {\n        return _owner;\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_function": "function renounceOwnership() public virtual onlyOwner {\n        _setOwner(address(0));\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_function": "function transferOwnership(address newOwner) public virtual onlyOwner {\n        require(newOwner != address(0),\"Ownable: new owner is the zero address\");\n        _setOwner(newOwner);\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable",
        "sol_function": "function _setOwner(address newOwner) private {\n        address oldOwner = _owner;\n        _owner = newOwner;\n        emit OwnershipTransferred(oldOwner,newOwner);\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that are not named `onlyOwner` and `onlyMinter`
  modifiers = Modifiers().without_names(["onlyOwner", "onlyMinter"]).exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP",
        "sol_modifier": "modifier onlyMinterOrOwner() {\n        require( (msg.sender == minter) || (msg.sender == owner()),'Sender is not the minter nor owner');\n        _;\n    }"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "RewardsDistributionRecipient",
        "sol_modifier": "modifier onlyRewardsDistribution() {\n        require(msg.sender == rewardsDistribution,\"Caller is not RewardsDistribution contract\");\n        _;\n    }"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "ReentrancyGuard",
        "sol_modifier": "modifier nonReentrant() {\n        \n        require(_status != _ENTERED,\"ReentrancyGuard: reentrant call\");\n\n        \n        _status = _ENTERED;\n\n        _;\n\n        \n        \n        _status = _NOT_ENTERED;\n    }"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "Pausable",
        "sol_modifier": "modifier notPaused {\n        require(!paused,\"This action cannot be performed while the contract is paused\");\n        _;\n    }"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "StakingRewards",
        "sol_modifier": "modifier notPaused {\n        require(!paused,\"This action cannot be performed while the contract is paused\");\n        _;\n    }"
    }
]
```
