# Callables.with\_names()

Adds a filter to get callables having specified names. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a single name, refer to [Callables.with\_name()](callables.with\_name.md).

To get all but some specified names, refer to [Callables.with\_names\_not()](callables.with\_names\_not.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions that are named `sendMessage` and `totalSupply`
  functions = Functions().with_names(["sendMessage", "totalSupply"]).exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0xB7ecef8430C7a35C522c76b7fEF192b4517b8bB5",
        "contract_name": "ICrossDomainMessenger",
        "sol_function": "function sendMessage(\n        address _target,bytes calldata _message,uint32 _gasLimit\n    ) external;"
    },
    {
        "contract": "0xeb5080232932DFf03088298233ddb9e8bF1D344f",
        "contract_name": "ICrossDomainMessenger",
        "sol_function": "function sendMessage(\n        address _target,bytes calldata _message,uint32 _gasLimit\n    ) external;"
    },
    {
        "contract": "0x0312c342aB049CeD994307C1d86B18ff61A22B54",
        "contract_name": "ICrossDomainMessenger",
        "sol_function": "function sendMessage(\n        address _target,bytes calldata _message,uint32 _gasLimit\n    ) external;"
    },
    {
        "contract": "0x5818840763Ee28ff0A3E3e8CB9eDeDd07Fb1Cd3f",
        "contract_name": "iOVM_CrossDomainMessenger",
        "sol_function": "function sendMessage(\n        address _target,bytes calldata _message,uint32 _gasLimit\n    ) external;"
    },
    {
        "contract": "0x5818840763Ee28ff0A3E3e8CB9eDeDd07Fb1Cd3f",
        "contract_name": "iOVM_L1CrossDomainMessenger",
        "sol_function": "function sendMessage(\n        address _target,bytes calldata _message,uint32 _gasLimit\n    ) external;"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that are named `onlyCaller` and `onlyClient`
  modifiers = Modifiers().with_names(["onlyCaller", "onlyClient"]).exec(100)

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
    },
    {
        "contract": "0x9aa1878934E222F116131D321F7cFd91f4A26d15",
        "contract_name": "EscrowClone",
        "sol_modifier": "modifier onlyClient() {\n        require(msg.sender == client);\n        _;\n    }"
    },
    {
        "contract": "0xdE8C117EE523615B6Ec057d504822694F1191509",
        "contract_name": "TransportationOffert",
        "sol_modifier": "modifier onlyClient(uint _index) {\n        require(msg.sender == Agreement_by_No[_index].client,\"Only Client can access this\");\n        _;\n    }"
    }
]
```
