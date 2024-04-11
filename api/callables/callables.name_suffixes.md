# Callables.name\_suffixes()

Adds a filter to get callables whose names have suffixes from the given list of suffixes. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a single prefix, refer to [Callables.name\_suffix()](callables.name\_suffix.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `Flashloan` or `cast` as suffix
  functions = Functions().name_suffixes(["Flashloan", "cast"]).exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0xDF1742fE5b0bFc12331D8EAec6b478DfDbD31464",
        "contract_name": "ValidationLogic",
        "sol_function": "function validateFlashloan(\n    address[] memory assets,uint256[] memory amounts,mapping(address => DataTypes.ReserveData) storage reservesData\n  ) internal view {\n    require(assets.length == amounts.length,Errors.INCONSISTENT_FLASHLOAN_PARAMS);\n    for (uint256 i = 0; i < assets.length; i++) {\n      DataTypes.ReserveConfigurationMap memory configuration = reservesData[assets[i]]\n        .configuration;\n      require(!configuration.getPaused(),Errors.RESERVE_PAUSED);\n      require(configuration.getActive(),Errors.RESERVE_INACTIVE);\n    }\n  }"
    },
    {
        "contract": "0x381917C6B653aCC25b244EeE2D6fF49CF9cEC76F",
        "contract_name": "FluidLeverage",
        "sol_function": "function withdrawViaFlashloan(uint256 _amt) external nonReentrant {\n    require(balanceOf(msg.sender) >= _amt,\"not-enough-bal\");\n\n    uint256 _scaledAmt = wmul(_amt,getIndex());\n    uint256 _multiplier = getCurrentLeverRatio().sub(1e18);\n    uint256 _amtToFlash = wmul(_scaledAmt,_multiplier);\n    uint256 _flashPremium = _amtToFlash.mul(AAVE_LENDING_POOL.FLASHLOAN_PREMIUM_TOTAL()).div(10000);\n    uint256 _amtToReturn = _scaledAmt.sub(_flashPremium);\n\n    if (collDecimals != 18) {\n      _amtToFlash = wmul(_amtToFlash,10 ** collDecimals);\n      _amtToReturn = wmul(_amtToReturn,10 ** collDecimals);\n    }\n\n    DataTypes.FlashloanData memory _data;\n    _data.opType = 3;\n    _data.flashAmt = _amtToFlash;\n    _data.flashAsset = address(COLLATERAL_ASSET);\n    _data.targetAsset = address(DEBT_ASSET);\n\n    _flashloan(address(COLLATERAL_ASSET),_amtToFlash,abi.encode(_data));\n    _withdrawCollateral(_amtToReturn,address(this));\n\n    (uint256 _fee,uint256 _finalAmt) = _calculateBurnFee(_amtToReturn);\n    COLLATERAL_ASSET.safeTransfer(feeCollector,_fee);\n    COLLATERAL_ASSET.safeTransfer(msg.sender,_finalAmt);\n\n    _burn(msg.sender,_amt);\n\n    \n  }"
    },
    {
        "contract": "0x000b30cf4206cbb3c5eb49523857feb24b5d206e",
        "contract_name": "Vm",
        "sol_function": "function broadcast() external;"
    },
    {
        "contract": "0x000b30cf4206cbb3c5eb49523857feb24b5d206e",
        "contract_name": "Vm",
        "sol_function": "function broadcast(address) external;"
    },
    {
        "contract": "0x000b30cf4206cbb3c5eb49523857feb24b5d206e",
        "contract_name": "Vm",
        "sol_function": "function startBroadcast() external;"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `Initialized` or `Open` as suffix
  modifiers = Modifiers().name_suffixes(["Initialized", "Open"]).exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x9C1283BdE77e4C67ea36373A752C7368b4F0A78d",
        "contract_name": "SquidGame",
        "sol_modifier": "modifier saleIsOpen() {\n    require(_totalSupply() <= MAX_ELEMENTS,'Sale end');\n    if (_msgSender() != owner()) {\n      require(!paused(),'Pausable: paused');\n    }\n    _;\n  }"
    },
    {
        "contract": "0x1648FAa9a5EAa6C7540c29B5EF01afCaFf3655Ec",
        "contract_name": "LoanPool",
        "sol_modifier": "modifier onlyPoolOpen() {\n        require(status == poolStatus.Opening,\"LPSC: CLOSED\");\n        _;\n    }"
    },
    {
        "contract": "0x2514daea66ada07a6b6c41eba6c6f514ba33bce6",
        "contract_name": "Creemees",
        "sol_modifier": "modifier saleIsOpen {\n        require(_totalSupply() <= MAX_ELEMENTS,\"Sale end\");\n        if (_msgSender() != owner()) {\n            require(!paused(),\"Pausable: paused\");\n        }\n        _;\n    }"
    },
    {
        "contract": "0x04123B815534354B5Aa578A7D8FA43F052066f60",
        "contract_name": "Pool",
        "sol_modifier": "modifier requireOpen() {\n        require(state == State.OPEN,\"state is not open\");\n        _;\n    }"
    },
    {
        "contract": "0x45136c2455Dd2631E31ab884cf167eC618CCf39a",
        "contract_name": "InitializableOwnable",
        "sol_modifier": "modifier notInitialized() {\n        require(!_INITIALIZED_,\"DODO_INITIALIZED\");\n        _;\n    }"
    }
]
```
