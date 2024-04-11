# Callables.with\_arg\_type()

Adds a filter to get callables having specified argument type. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a list of argument types, refer to [Callables.with\_arg\_types()](callables.with\_arg\_types.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `Order` as one of their argument types
  functions = Functions().with_arg_type("Order").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0xC315Bb336bB5F82c1fd21989013b4B302a69c563",
        "contract_name": "Board",
        "sol_function": "function make(Order calldata o) external returns (uint id) {\n        require(o.owner == msg.sender,'board/not-owner');\n        require(o.expires > block.timestamp,'board/too-late');\n        require(o.expires <= block.timestamp + TTL,'board/too-long');\n        require(o.baseAmt >= o.minBaseAmt,'board/min-base-too-big');\n        id = next++;\n        orders[id] = getHash(o);\n        emit Make(id,o);\n    }"
    },
    {
        "contract": "0xC315Bb336bB5F82c1fd21989013b4B302a69c563",
        "contract_name": "Board",
        "sol_function": "function take(uint id,uint baseAmt,Order calldata o) external {\n        require(orders[id] == getHash(o),'board/wrong-hash');\n        require(o.expires > block.timestamp,'board/expired');\n        require(baseAmt <= o.baseAmt,'board/base-too-big');\n        require(baseAmt >= o.minBaseAmt || baseAmt == o.baseAmt,'board/base-too-small');\n\n        uint one = 10 ** uint(o.baseDecimals);\n        uint rounding = !o.buying && (baseAmt * o.price) % one > 0 ? one : 0;\n        uint quoteAmt = (baseAmt * o.price + rounding) / one;\n\n        if(baseAmt < o.baseAmt) {\n            Order memory n = o;\n            n.baseAmt = n.baseAmt - baseAmt;\n            orders[id] = getHash(n);\n        } else {\n            delete orders[id];\n        }\n\n        emit Take(msg.sender,id,baseAmt,quoteAmt);\n\n        if(o.buying) {\n            safeTransferFrom(ERC20(o.baseTkn),msg.sender,o.owner,baseAmt);\n            safeTransferFrom(ERC20(o.quoteTkn),o.owner,msg.sender,quoteAmt);\n\n        } else {\n            safeTransferFrom(ERC20(o.baseTkn),o.owner,msg.sender,baseAmt);\n            safeTransferFrom(ERC20(o.quoteTkn),msg.sender,o.owner,quoteAmt);\n        }\n    }"
    },
    {
        "contract": "0xC315Bb336bB5F82c1fd21989013b4B302a69c563",
        "contract_name": "Board",
        "sol_function": "function cancel(uint id,Order calldata o) external {\n        require(orders[id] == getHash(o),'board/wrong-hash');\n        require(o.expires <= block.timestamp || o.owner == msg.sender,'board/invalid-cancel');\n        delete orders[id];\n        emit Cancel(msg.sender,id);\n    }"
    },
    {
        "contract": "0xC315Bb336bB5F82c1fd21989013b4B302a69c563",
        "contract_name": "Board",
        "sol_function": "function getHash(Order memory o) private pure returns (bytes32) {\n        return keccak256(abi.encode(\n            o.baseTkn,o.quoteTkn,o.baseDecimals,o.buying,o.owner,o.expires,o.baseAmt,o.price,o.minBaseAmt\n        ));\n    }"
    },
    {
        "contract": "0xa8f909d55c16a27a6f89cbf1952cdbbf9e244204",
        "contract_name": "Board",
        "sol_function": "function make(Order calldata o) external returns (uint id) {\n        require(o.owner == msg.sender,'board/not-owner');\n        require(o.expires > block.timestamp,'board/too-late');\n        require(o.expires < block.timestamp + TTL,'board/too-long');\n        require(o.baseAmt >= o.minBaseAmt,'board/min-base-too-big');\n        id = next++;\n        orders[id] = getHash(o);\n        emit Make(id,o);\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `Set` as one of their argument types
  modifiers = Modifiers().with_arg_type("State").exec(100)

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
    },
    {
        "contract": "0x7f62DB88eB9BE16D1B597094bDC3f5Ad84D3B6ea",
        "contract_name": "Lists",
        "sol_modifier": "modifier isContractState(State _state) {\n      require (\n        state == _state,\"contract state is not valid\"\n      );\n      _;\n    }"
    }
]
```
