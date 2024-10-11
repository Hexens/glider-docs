---
description: Return the value representing the salt parameter of the contract creation call
---

# Call.get\_call\_salt()

`get_call_salt() ->` [`APIList`](../../iterables/apilist.md)`[Union[`[`Value`](../)`,` [`NoneObject`](../../internal/noneobject/)`]]`

The function returns the Value (or any derived class) that represents the special salt parameter used in contract creation calls; the list will be empty if the call is not a contract creation or does not have a salt parameter.

For example, in the instruction:

```solidity
pool = address(new UniswapV3Pool{salt: keccak256(abi.encode(token0, token1, fee))}());
```

the contract creation call:

```solidity
new UniswapV3Pool{salt: keccak256(abi.encode(token0, token1, fee))}
```

has a salt parameter:&#x20;

```solidity
keccak256(abi.encode(token0, token1, fee))
```

the function will return the value representing this expression (and it will be of type [Call](./) in this case, as its a keccak256 function call)

**Query Example**

```python
from glider import *

def query():
    instructions = (
        Contracts()
        .with_name("UniswapV3PoolDeployer")
        .functions()
        .with_name("deploy")
        .instructions()
        .exec(10)
        .filter(lambda x: x.is_new_contract())
    )


    for ins in instructions:
        print(ins.get_value().get_callee_values()[0].get_call_salt())
        print(ins.get_value().get_callee_values()[0].get_call_salt().expression)

    return instructions
```

**Output Example**

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>
