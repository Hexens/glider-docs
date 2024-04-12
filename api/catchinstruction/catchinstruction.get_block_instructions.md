# CatchInstruction.get\_block\_instructions()

`get_block_instructions() → List[`[`Instruction`](../instruction/)`]`

Returns all instructions from the catch block

## Example

```python
from glider import *

def query():
  instructionlist = Instructions().catch_instructions().exec(1,1)
  
  return instructionlist[0].get_block_instructions()
```

## Output

```solidity
"root":{4 items
"contract":string"0x6f9f14e160282A3D613eD2af3cB579DE4bfC7c1e"
"contract_name":string"ERC1155"
"sol_function":solidity
function _doSafeTransferAcceptanceCheck(
        address operator,address from,address to,uint256 id,uint256 amount,bytes memory data
    ) private {
        if (to.isContract()) {
            try IERC1155Receiver(to).onERC1155Received(operator,from,id,amount,data) returns (bytes4 response) {
                if (response != IERC1155Receiver.onERC1155Received.selector) {
                    revert("ERC1155: ERC1155Receiver rejected tokens");
                }
            } catch Error(string memory reason) {
                revert(reason);
            } catch {
                revert("ERC1155: transfer to non ERC1155Receiver implementer");
            }
        }
    }
"sol_instruction":solidity
revert(reason)
}
```

\
