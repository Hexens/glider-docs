---
description: Returns parent function/modifier of the argument.
---

# Argument.get\_parent()

## Return type:

* [Callable](../callable/)

## Example Query

```python
from glider import *
def query():
    func = (Contracts()
    .with_name('Pair')
    .non_interface_contracts()
    .functions()
    .with_arg_count(1)
    .exec(1)[0])
    arg = func.arguments().list()[0]
    
    print(arg.source_code())
    print(arg.get_parent().source_code())
    return []
```

## Output

```solidity
"root":{1 item
"print_output":[2 items
0:string"uint256 tokenId"
1:string"function withdraw(uint256 tokenId) public {
        // check that the sender is the caviar owner
        require(caviar.owner() == msg.sender, "Withdraw: not owner");

        // check that the close period has been set
        require(closeTimestamp != 0, "Withdraw not initiated");

        // check that the close grace period has passed
        require(block.timestamp >= closeTimestamp, "Not withdrawable yet");

        // transfer the nft to the caviar owner
        ERC721(nft).safeTransferFrom(address(this), msg.sender, tokenId);

        emit Withdraw(tokenId);
    }"
]
}
```
