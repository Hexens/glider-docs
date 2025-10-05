---
description: >-
  Returns a Functions object representing the functions through which the
  function could be called
---

# Callable.callee\_functions\_recursive()

`callee_functions_recursive() ->` [`Functions`](../callables/functions/)

The function is the _recursive_/_inter-procedural_ variant of [callee\_functions()](callable.callee_functions.md), meaning it works recursively. It returns the Functions object representing all the functions through which the function could be called.&#x20;

The difference between `callee_functions_recursive()` and `callee_functions()` the later one will only return direct callee functions, while the **recursive** version will find all the functions recursively that eventually call the target function.

## Query Example

```python
from glider import *


def query():
    functions = Functions().with_name("requestRandomness").exec(1)

    return functions[0].callee_functions_recursive().exec()
```

For the function:

```solidity
function requestRandomness(bytes32 _keyHash,uint256 _fee,uint256 _seed)
    public returns (bytes32 requestId)
  {
    LINK.transferAndCall(vrfCoordinator,_fee,abi.encode(_keyHash,_seed));
    
    uint256 vRFSeed  = makeVRFInputSeed(_keyHash,_seed,address(this),nonces[_keyHash]);
    
    nonces[_keyHash] = nonces[_keyHash].add(1);
    return makeRequestId(_keyHash,vRFSeed);
  }
```

The output will be:

## Example Output

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-21 at 12.38.28 PM.png" alt=""><figcaption></figcaption></figure>
