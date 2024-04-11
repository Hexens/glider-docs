# Callables.with\_arg\_name()

Adds a filter to get callables having specified argument name. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `_address` as one of their arguments
  functions = Functions().with_arg_name("_address").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "Permissions",
        "sol_function": "function isMinter(address _address) external view override returns (bool) {\n        return hasRole(MINTER_ROLE,_address);\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "Permissions",
        "sol_function": "function isBurner(address _address) external view override returns (bool) {\n        return hasRole(BURNER_ROLE,_address);\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "Permissions",
        "sol_function": "function isPCVController(address _address)\n        external\n        view\n        override\n        returns (bool)\n    {\n        return hasRole(PCV_CONTROLLER_ROLE,_address);\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "Permissions",
        "sol_function": "function isGovernor(address _address)\n        public\n        view\n        virtual\n        override\n        returns (bool)\n    {\n        return hasRole(GOVERN_ROLE,_address);\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "Permissions",
        "sol_function": "function isGuardian(address _address) public view override returns (bool) {\n        return hasRole(GUARDIAN_ROLE,_address);\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `_caller` as one of their arguments
  modifiers = Modifiers().with_arg_name("_caller").exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x36A34224E227a7c32F2c3F35C7Cb47618434C02D",
        "contract_name": "SavingsAccount",
        "sol_modifier": "modifier onlyCreditLine(address _caller) {\n        require(_caller == creditLine,'Invalid caller');\n        _;\n    }"
    },
    {
        "contract": "0x845735e8ee0f60ea81704903ecad39a2d40341e1",
        "contract_name": "Controller",
        "sol_modifier": "modifier onlyAllowedCreator(address _caller) {\n        require(isAllowedCreator(_caller),\"not allowed\");\n        _;\n    }"
    },
    {
        "contract": "0x76c4886eca8e82b6A01F04715E1479cA64a54b92",
        "contract_name": "Inventory",
        "sol_modifier": "modifier isTokenOwner(address _caller,uint256 _tokenId) {\n        require(\n            balanceOf(_caller,_tokenId) != 0,\"caller doesn't own this token\"\n        );\n        _;\n    }"
    },
    {
        "contract": "0xddfE9569A7C682A096805972cFCC70945f0d17a6",
        "contract_name": "SavingsAccount",
        "sol_modifier": "modifier onlyCreditLine(address _caller) {\n        require(_caller == creditLine,'Invalid caller');\n        _;\n    }"
    },
    {
        "contract": "0xfca4423a1a3fcea7eea493566ec4e6bbcb80b583",
        "contract_name": "BaseExtension",
        "sol_modifier": "modifier onlyAllowedCaller(address _caller) {\n        require(isAllowedCaller(_caller),\"Address not permitted to call\");\n        _;\n    }"
    }
]
```
