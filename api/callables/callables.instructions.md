# Callables.instructions()

Returns the [Instructions](../instructions/) object for the instructions of the callables. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the instructions of a list of functions
  instructions = Functions().instructions().exec(100)

  # Return the first five instructions
  return instructions[0:5]
```

Output:

```json
[
    {
        "contract": "0x4625e433ab85fEdBE510873AE46e391754a40DeE",
        "contract_name": "console",
        "sol_function": "function log(string memory p0,bool p1,uint p2,uint p3) internal view {\n\t\t_sendLogPayload(abi.encodeWithSignature(\"log(string,bool,uint,uint)\",p0,p1,p2,p3));\n\t}",
        "sol_instruction": "{\n\t\t_sendLogPayload(abi.encodeWithSignature(\"log(string,bool,uint,uint)\",p0,p1,p2,p3));\n\t}"
    },
    {
        "contract": "0x4625e433ab85fEdBE510873AE46e391754a40DeE",
        "contract_name": "console",
        "sol_function": "function log(string memory p0,bool p1,uint p2,uint p3) internal view {\n\t\t_sendLogPayload(abi.encodeWithSignature(\"log(string,bool,uint,uint)\",p0,p1,p2,p3));\n\t}",
        "sol_instruction": "_sendLogPayload(abi.encodeWithSignature(\"log(string,bool,uint,uint)\",p0,p1,p2,p3))"
    },
    {
        "contract": "0x2Fe7Cf1D80F471C4049513Bc169961b1aF2d51C3",
        "contract_name": "BridgePool",
        "sol_function": "function _getProposerBond(uint256 amount) private view returns (uint256) {\n        return _getAmountFromPct(bridgeAdmin.proposerBondPct(),amount);\n    }",
        "sol_instruction": "{\n        return _getAmountFromPct(bridgeAdmin.proposerBondPct(),amount);\n    }"
    },
    {
        "contract": "0x2Fe7Cf1D80F471C4049513Bc169961b1aF2d51C3",
        "contract_name": "BridgePool",
        "sol_function": "function _getProposerBond(uint256 amount) private view returns (uint256) {\n        return _getAmountFromPct(bridgeAdmin.proposerBondPct(),amount);\n    }",
        "sol_instruction": "return _getAmountFromPct(bridgeAdmin.proposerBondPct(),amount)"
    },
    {
        "contract": "0xe0Dd5841B5B83631d4EaDb84BF0307e0e80F5C6f",
        "contract_name": "CoinToken",
        "sol_function": "function reflectionFromToken(uint256 tAmount,bool deductTransferFee) public view returns(uint256) {\n        require(tAmount <= _tTotal,\"Amount must be less than supply\");\n        if (!deductTransferFee) {\n            (uint256 rAmount,,,,,,) = _getValues(tAmount);\n            return rAmount;\n        } else {\n            (,uint256 rTransferAmount,,,,,) = _getValues(tAmount);\n            return rTransferAmount;\n        }\n    }",
        "sol_instruction": "{\n        require(tAmount <= _tTotal,\"Amount must be less than supply\");\n        if (!deductTransferFee) {\n            (uint256 rAmount,,,,,,) = _getValues(tAmount);\n            return rAmount;\n        } else {\n            (,uint256 rTransferAmount,,,,,) = _getValues(tAmount);\n            return rTransferAmount;\n        }\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the instructions of a list of modifiers
  instructions = Modifiers().instructions().exec(100)

  # Return the first five instructions
  return instructions[0:5]
```

Output:

```json
[
    {
        "contract": "0x811d458ecC8a2aC69D13B24b22B8740FD3ce23ba",
        "contract_name": "AlloyVault",
        "sol_function": "modifier whenVaultNotStarted() {\n    require(!vaultStarted,\"Vault has already start accepting deposits\");\n    _;\n  }",
        "sol_instruction": "{\n    require(!vaultStarted,\"Vault has already start accepting deposits\");\n    _;\n  }"
    },
    {
        "contract": "0x811d458ecC8a2aC69D13B24b22B8740FD3ce23ba",
        "contract_name": "AlloyVault",
        "sol_function": "modifier whenVaultNotStarted() {\n    require(!vaultStarted,\"Vault has already start accepting deposits\");\n    _;\n  }",
        "sol_instruction": "require(!vaultStarted,\"Vault has already start accepting deposits\")"
    },
    {
        "contract": "0x811d458ecC8a2aC69D13B24b22B8740FD3ce23ba",
        "contract_name": "AlloyVault",
        "sol_function": "modifier whenVaultNotStarted() {\n    require(!vaultStarted,\"Vault has already start accepting deposits\");\n    _;\n  }",
        "sol_instruction": "_"
    },
    {
        "contract": "0xe8fa80c8e21713605a7f3bcbbf3d42f8dd820e8c",
        "contract_name": "Scorefam",
        "sol_function": "modifier initializer() {\n        require(\n            _initializing || !_initialized,\"Initializable: contract is already initialized\"\n        );\n\n        bool isTopLevelCall = !_initializing;\n        if (isTopLevelCall) {\n            _initializing = true;\n            _initialized = true;\n        }\n\n        _;\n\n        if (isTopLevelCall) {\n            _initializing = false;\n        }\n    }",
        "sol_instruction": "{\n        require(\n            _initializing || !_initialized,\"Initializable: contract is already initialized\"\n        );\n\n        bool isTopLevelCall = !_initializing;\n        if (isTopLevelCall) {\n            _initializing = true;\n            _initialized = true;\n        }\n\n        _;\n\n        if (isTopLevelCall) {\n            _initializing = false;\n        }\n    }"
    },
    {
        "contract": "0xe8fa80c8e21713605a7f3bcbbf3d42f8dd820e8c",
        "contract_name": "Scorefam",
        "sol_function": "modifier initializer() {\n        require(\n            _initializing || !_initialized,\"Initializable: contract is already initialized\"\n        );\n\n        bool isTopLevelCall = !_initializing;\n        if (isTopLevelCall) {\n            _initializing = true;\n            _initialized = true;\n        }\n\n        _;\n\n        if (isTopLevelCall) {\n            _initializing = false;\n        }\n    }",
        "sol_instruction": "require(\n            _initializing || !_initialized,\"Initializable: contract is already initialized\"\n        )"
    }
]
```
