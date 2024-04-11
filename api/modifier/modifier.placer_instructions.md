# Modifier.placer\_instructions()

Returns placeholder [instructions](../instruction/) of the [modifier](./).

## Return type

→ List\[[Instruction](../instruction/)]

An example of a query which can analyze placeholder instructions is:

```python
from glider import *
def query():
  modifierlist = Modifiers()\
      .name_prefix("check")\
      .exec(5)
  
  results =  []

  for modd in modifierlist:
    for placers in modd.placer_instructions():
      results.append(placers)

  return results

```

## Output

```json
"root":{4 items
"contract":string"0x2D76FCCC67645A61794cB65584c5e89A9f3945Ed"
"contract_name":string"CommonBudgetApproval"
"sol_function":solidity
modifier checkTime(uint256 id) {
        require(block.timestamp <= transactions[id].deadline,"Transaction expired");
        require(block.timestamp >= startTime,"Budget usage period not started");
        if(endTime != 0) {
            require(block.timestamp < endTime,"Budget usage period has ended");
        }
        _;
    }
"sol_instruction":solidity
_
}
"root":{4 items
"contract":string"0x2D76FCCC67645A61794cB65584c5e89A9f3945Ed"
"contract_name":string"TransferERC20BudgetApproval"
"sol_function":solidity
modifier checkTime(uint256 id) {
        require(block.timestamp <= transactions[id].deadline,"Transaction expired");
        require(block.timestamp >= startTime,"Budget usage period not started");
        if(endTime != 0) {
            require(block.timestamp < endTime,"Budget usage period has ended");
        }
        _;
    }
"sol_instruction":solidity
_
}
"root":{4 items
"contract":string"0xa4bE27abf18D18f3F86Ec2EE3039880402f89aE8"
"contract_name":string"KCGStaking"
"sol_function":solidity
modifier checkStakingTimeframe(uint256 timeframe) {
        require(timeframe == FOURTY_FIVE_DAYS || timeframe == NINETY_DAYS || timeframe == ONE_HUNDREDS_EIGHTY_DAYS,"invalid staking timeframe");
        _;
    }
"sol_instruction":solidity
_
}
"root":{4 items
"contract":string"0x254f997e66eEdB84b6e5833ca494bE90Eb0330e6"
"contract_name":string"BetaBank"
"sol_function":solidity
modifier checkPID(address _owner,uint _pid) {
    require(_pid < nextPositionIds[_owner],'BetaBank/checkPID');
    _;
  }
"sol_instruction":solidity
_
}
"root":{4 items
"contract":string"0x07ac2e0fa5944c81f66dc54d3d54d58f04bb5d10"
"contract_name":string"KCGStaking"
"sol_function":solidity
modifier checkArgsLength(uint256[] calldata tokenIds,uint256[] calldata timeframe) {
        require(tokenIds.length == timeframe.length,"token ids and time frame must be same length");
        _;
    }
"sol_instruction":solidity
_
}
```
