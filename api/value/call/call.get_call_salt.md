---
description: Return the value representing the salt parameter of the contract creation call
---

# Call.get\_call\_salt()

`get_call_salt() → List[`[`Value`](../)`]`

The function returns the Value (or any derived class) that represents the special salt parameter used in contract creation calls; the list will be empty if the call is not a contract creation or does not have a salt parameter.

For example, in the instruction:

```solidity
lmPool = new PancakeV3LmPool{salt: keccak256(abi.encode(address(pool), masterChef, block.timestamp))}();
```

the contract creation call:

```solidity
new PancakeV3LmPool{salt: keccak256(abi.encode(address(pool), masterChef, block.timestamp))}();
```

has a salt parameter:&#x20;

```solidity
keccak256(abi.encode(address(pool), masterChef, block.timestamp))
```

the function will return the value representing this expression (and it will be of type [Call](./) in this case, as its a keccak256 function call)

**Query Example**

```python
from glider import *

def query():
  instructions = Functions().with_name('deploy').instructions().calls().exec(1000)

  output = []

  for instruction in instructions:
    for call in instruction.get_callee_values():
        for salt in call.get_call_salt():
          output.append(instruction)
          print(salt, salt.expression)
          return [instruction]

  return output
```

**Output**

```solidity
"root":{4 items
"contract":string"0xbebb526e8e197b3ba317573e6653c5a1ec0a3829"
"contract_name":string"PancakeV3LmPoolDeployer"
"sol_function":solidity
function deploy(IPancakeV3PoolWithLMPool pool) external onlyOwner returns (IPancakeV3LmPool lmPool) {
        require(whiteList[address(pool)], 'Not in whiteList');
 
        require(!LMPoolUpdateFlag[address(pool)], 'Already Updated');
        LMPoolUpdateFlag[address(pool)] = true;
 
        address secondLMPool = pool.lmPool();
        address firstLMPool = ILMPool(secondLMPool).OldLMPool();
        parameters = Parameters({
            pool: address(pool),
            masterChef: masterChef,
            firstLMPool: firstLMPool,
            secondLMPool: secondLMPool
        });
 
        lmPool = new PancakeV3LmPool{salt: keccak256(abi.encode(address(pool), masterChef, block.timestamp))}();
 
        delete parameters;
 
        // Set new LMPool for pancake v3 pool.
        IPancakeV3Factory(INonfungiblePositionManager(IMasterChefV3(masterChef).nonfungiblePositionManager()).factory())
            .setLmPool(address(pool), address(lmPool));
 
        // Initialize the new LMPool.
        lmPool.initialize();
 
        emit NewLMPool(address(pool), address(lmPool));
    }
"sol_instruction":solidity
lmPool = new PancakeV3LmPool{salt: keccak256(abi.encode(address(pool), masterChef, block.timestamp))}()
}
"root":{1 item
"print_output":[2 items
0:string"<api.value.Call object at 0x7f9e659a5910>"
1:string"keccak256(bytes)(abi.encode(address(pool),masterChef,block.timestamp))"
]
}
```
