---
description: >-
  Returns a list of CallNodes whose corresponding functions call the current
  node's corresponding function.
---

# CallNode.callers()

`callers() →` [`APIList`](../../iterables/apilist.md)`[`[`CallNode`](./)`]`

## Query Example

```python
from glider import *

def query():
    data = []
    instructions = Instructions().with_callee_function_name_prefix('burn').exec(10)

    for instruction in instructions:
        if len(data) > 0:
            break # demo first result only
        functionContainsBurn = instruction.get_parent() #api.functions.Function (*)
        contract = functionContainsBurn.get_contract() #api.contracts.Contract
        call_graph = contract.call_graph() #api.call_graph.CallGraph 
        nodes = call_graph.nodes() #Dict[str, CallNode]
        for id in nodes:
            if(id != functionContainsBurn.db_id):
                continue
        callers = nodes[id].callers() # APIList[CallNode]
        if len(callers) > 0:
            print(functionContainsBurn.source_code())
            for caller in callers:
                print("caller: " + caller.callable_name())
            data.append(instruction)

    return data
```

## Example Output

```solidity
{
  "print_output": [
    function createStakingPool(
            IERC20 _stakingToken,IERC20 _poolToken,uint256 _startTime,uint256 _finishTime,uint256 _poolTokenAmount,bool _hasWhitelisting
        ) external {
    
            if(feeAmount > 0) {
                uint256 burnAmount = feeAmount.mul(burnPercent).div(divider);
    
                feeToken.safeTransferFrom(
                    msg.sender,feeWallet,feeAmount.sub(burnAmount)
                );
                
                if(burnAmount > 0) {
                    feeToken.safeTransferFrom(msg.sender,address(this),burnAmount);
                    feeToken.burn(burnAmount);
                }
            }
    
            StakingPool stakingPool =
                new StakingPool(
                    _stakingToken,_poolToken,_startTime,_finishTime,_poolTokenAmount,_hasWhitelisting
                );
            stakingPool.transferOwnership(msg.sender);
    
            _poolToken.safeTransferFrom(
                msg.sender,address(stakingPool),_poolTokenAmount
            );
            
            require(_poolToken.balanceOf(address(stakingPool)) == _poolTokenAmount,"Unsupported token");
    
            emit StakingPoolCreated(msg.sender,address(stakingPool),address(_stakingToken),address(_poolToken),_startTime,_finishTime,_poolTokenAmount);
    }    
    "caller: _mint",
    "caller: _burn",
    "caller: _transfer"
  ]
}
```
