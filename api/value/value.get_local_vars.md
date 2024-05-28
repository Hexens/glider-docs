---
description: >-
  Returns a list of Var objects of current value whose corresponding object is a
  LocalVariable.
---

# Value.get\_local\_vars()

`get_local_vars() -> List[`[`Var`](var/)`]`

The function returns all the local variables used (read/written) inside the Value.

## Query Example

```python
from glider import *

def query():
	functions = Functions()\
		.with_name('stake')\
		.exec(2)
	
	for function in functions:
		for instruction in function.instructions().exec():
			for operand in instruction.get_operands():
				local_vars = operand.get_local_vars()
				if len(local_vars)>0:
					print([x.expression for x in local_vars])
	return functions

```

## Example Output

```solidity
"root":{3 items
"contract":string"0x11faf8f647602f923672e2455322107a27acf9c1"
"contract_name":string"StakingContract"
"sol_function":solidity
function stake(address _collection, uint256[] calldata tokenIds) public nonReentrant {
        require(allowedToStake[_collection], "Not allowed to stake for this collection");
        require(tokenIds.length > 0, "tokenIds parameter has zero length.");
        uint256 _pendingRewards = pendingReward(_collection, msg.sender);
        if(_pendingRewards > 0) {
            require(rtoken.transfer(msg.sender, _pendingRewards), "Reward Token Transfer is failed.");
        }
        userInfo[_collection][msg.sender].startBlock = block.number;

        for(uint256 i = 0; i < tokenIds.length; i++) {
            require(IERC721(_collection).ownerOf(tokenIds[i]) == msg.sender, "Not Your NFT.");
            IERC721(_collection).transferFrom(msg.sender, address(this), tokenIds[i]);
            EnumerableSet.add(userInfo[_collection][msg.sender].tokenIds, tokenIds[i]);
        }
        emit Stake(msg.sender, tokenIds.length);
    }
}
"root":{1 item
"print_output":[7 items
0:string"['_pendingRewards']"
1:string"['_pendingRewards']"
2:string"['i']"
3:string"['i']"
4:string"['i']"
5:string"['i']"
6:string"['i']"
]
}
```
