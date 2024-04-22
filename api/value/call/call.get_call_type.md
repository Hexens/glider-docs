---
description: Returns the type of the call
---

# Call.get\_call\_type()

`get_call_type() → CallType`

The Call represents all types of call values: external, internal, log emit, etc. This function can be used to get the type of the call.

**Query Example**

```python
from glider import *

def query():
  instructions = Functions().with_name('deploy').instructions().calls().exec(2)

  for instruction in instructions:
    for call in instruction.get_callee_values():
        print(call.expression, call.get_call_type())

  return instructions
```

**Output**

```solidity
"root":{4 items
"contract":string"0xfd3a7db79f31a3acf47951dc3e61155c1ec4e3b4"
"contract_name":string"StakingRewardsFactory"
"sol_function":solidity
function deploy(address stakingToken, uint rewardAmount) public onlyOwner {
        StakingRewardsInfo storage info = stakingRewardsInfoByStakingToken[stakingToken];
        require(info.stakingRewards == address(0), 'StakingRewardsFactory::deploy: already deployed');
 
        info.stakingRewards = address(new StakingRewards(/*_rewardsDistribution=*/ address(this), rewardsToken, stakingToken));
        info.rewardAmount = rewardAmount;
        stakingTokens.push(stakingToken);
    }
"sol_instruction":solidity
require(info.stakingRewards == address(0), 'StakingRewardsFactory::deploy: already deployed')
}
"root":{4 items
"contract":string"0xfd3a7db79f31a3acf47951dc3e61155c1ec4e3b4"
"contract_name":string"StakingRewardsFactory"
"sol_function":solidity
function deploy(address stakingToken, uint rewardAmount) public onlyOwner {
        StakingRewardsInfo storage info = stakingRewardsInfoByStakingToken[stakingToken];
        require(info.stakingRewards == address(0), 'StakingRewardsFactory::deploy: already deployed');
 
        info.stakingRewards = address(new StakingRewards(/*_rewardsDistribution=*/ address(this), rewardsToken, stakingToken));
        info.rewardAmount = rewardAmount;
        stakingTokens.push(stakingToken);
    }
"sol_instruction":solidity
info.stakingRewards = address(new StakingRewards(/*_rewardsDistribution=*/ address(this), rewardsToken, stakingToken))
}
"root":{1 item
"print_output":[4 items
0:string"require(bool,string)(info.stakingRewards == address(0),"StakingRewardsFactory::deploy: already deployed")"
1:string"CallType.SOLIDITY"
2:string"new StakingRewards(address(this),rewardsToken,stakingToken)"
3:string"CallType.PUBLIC"
]
}
```

As can be seen in the example above, the call:

```solidity
require(info.stakingRewards == address(0), 'StakingRewardsFactory::deploy: already deployed')
```

has returned call type of CallType.SOLIDITY, and the call:

```solidity
new StakingRewards(address(this),rewardsToken,stakingToken)
```

returned call type CallType.PUBLIC, as the call is a contract creation call, it will follow its constructor function (if possible) and inherit the type of the call from it.
