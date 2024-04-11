# Callables.with\_arg\_types()

Adds a filter to get callables having specified argument types. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a single argument type, refer to [Callables.with\_arg\_type()](callables.with\_arg\_type.md).

_Note that the order of the argument types is important. I.e. calling `.with_arg_types(["a", "b"])` is **not equivalent** to calling `.with_arg_types(["b", "a"])` !_

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `uint256` and `address` as argument types
  functions = Functions().with_arg_types(["uint256", "address"]).exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x3450955Ffe1e8DE92c7348a497d7Fc2C9283ff3d",
        "contract_name": "console",
        "sol_function": "function log(uint p0,address p1) internal view {\n\t\t_sendLogPayload(abi.encodeWithSignature(\"log(uint,address)\",p0,p1));\n\t}"
    },
    {
        "contract": "0x069eB24159BcD26eE776Be2d8Af987bD4564F398",
        "contract_name": "OlympusStaking",
        "sol_function": "function stake( uint _amount,address _recipient ) external returns ( bool ) {\n        rebase();\n        \n        IERC20( OHM ).safeTransferFrom( msg.sender,address(this),_amount );\n\n        Claim memory info = warmupInfo[ _recipient ];\n        require( !info.lock,\"Deposits for account are locked\" );\n\n        warmupInfo[ _recipient ] = Claim ({\n            deposit: info.deposit.add( _amount ),gons: info.gons.add( IsOHM( sOHM ).gonsForBalance( _amount ) ),expiry: epoch.number.add( warmupPeriod ),lock: false\n        });\n        \n        IERC20( sOHM ).safeTransfer( warmupContract,_amount );\n        return true;\n    }"
    },
    {
        "contract": "0x5D2b5eA79Cb44396659468c29B407CC7C1F6aE3f",
        "contract_name": "console",
        "sol_function": "function log(uint p0,address p1) internal view {\n\t\t_sendLogPayload(abi.encodeWithSignature(\"log(uint,address)\",p0,p1));\n\t}"
    },
    {
        "contract": "0x900fDa4E261fF0d248B8B81D52950a0c8aD14A2e",
        "contract_name": "console",
        "sol_function": "function log(uint p0,address p1) internal view {\n\t\t_sendLogPayload(abi.encodeWithSignature(\"log(uint,address)\",p0,p1));\n\t}"
    },
    {
        "contract": "0xb552632a9F287Bf46c296052867d588636aF26BC",
        "contract_name": "TokenFarm",
        "sol_function": "function stakeTokens(uint256 _amount,address _token) public {\n        \n        \n        \n        require(_amount > 0,\"Amount must be more than zero!\");\n        \n        require(tokenIsAllowed(_token),\"Token is currently not allowed!\");\n        \n        \n        IERC20(_token).transferFrom(msg.sender,address(this),_amount);\n        \n        updateUniqueTokensStaked(msg.sender,_token);\n        stakingBalance[_token][msg.sender] =\n            stakingBalance[_token][msg.sender] +\n            _amount;\n        \n        if (uniqueTokensStaked[msg.sender] == 1) {\n            stakers.push(msg.sender);\n        }\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `uint256` and `State` as their argument types
  modifiers = Modifiers().with_arg_types(["uint256", "State"]).exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x7f62DB88eB9BE16D1B597094bDC3f5Ad84D3B6ea",
        "contract_name": "Lists",
        "sol_modifier": "modifier isListState(uint _id,State _state) {\n      require (\n        idToList[_id].state == _state,\"list state is not valid\"\n      );\n      _;\n    }"
    }
]
```
