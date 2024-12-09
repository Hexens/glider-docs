---
description: Returns true if the instruction creates a new contract.
---

# Instruction.is\_new\_contract()

`is_new_contract() -> bool`

## Query Example

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .exec(1500)
        .filter(lambda inst : inst.is_new_contract())
    )
            
    return instructions
```

## Output Example

```solidity
[
  {
    "contract": "0xe5fA13058EdE558a2bFA675043f175148858A5F6",
    "contract_name": "StakeMaster",
    "contract_link": "",
    "uuid": "f51c4d56-0396-43d6-bd05-21060adb247c",
    "severity": "",
    "sol_function": 
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
    "sol_instruction": 
      StakingPool stakingPool =
          new StakingPool(
              _stakingToken,_poolToken,_startTime,_finishTime,_poolTokenAmount,_hasWhitelisting
          );
  }
]
```
