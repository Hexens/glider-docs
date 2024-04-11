# MethodProp.IS\_PAYABLE

In a smart contract a function can be marked as payable. This means that the function can accept the native token of the chain as a payment value.

An example  of a payable function is

```solidity
function depositETH() external payable {
	depositor[msg.sender].balance = msg.value;
}
```

An example of a query which would select all payable functions is:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_PAYABLE]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

```json
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"LTP"
"sol_function":solidity
function issueNft(address to,uint256 tokenId,uint256 amount,string memory tokenURI) external payable onlyMinterOrOwner { 
        
        require(to != address(this),"Issue to a new address");
        require(ownerOf(tokenId) == address(this),"NFT already issued");
        
        
 
        _setTokenURI(nextId,tokenURI);
        this.safeTransferFrom(address(this),to,tokenId);
        emit NFTIssued(tokenId,to,tokenURI);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"LTP"
"sol_function":solidity
function withdrawETH() external payable onlyOwner {
        payable(msg.sender).transfer(address(this).balance);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"LTP"
"sol_function":solidity
function paymegas() external payable {
        
    }
}
"root":{3 items
"contract":string"0x561ae3768ee95987b355c287f985f2838f01e632"
"contract_name":string"IUniswapV2Router01"
"sol_function":solidity
function addLiquidityETH(
        address token,uint amountTokenDesired,uint amountTokenMin,uint amountETHMin,address to,uint deadline
    ) external payable returns (uint amountToken,uint amountETH,uint liquidity);
}
"root":{3 items
"contract":string"0x561ae3768ee95987b355c287f985f2838f01e632"
"contract_name":string"IUniswapV2Router01"
"sol_function":solidity
function swapExactETHForTokens(uint amountOutMin,address[] calldata path,address to,uint deadline)
        external
        payable
        returns (uint[] memory amounts);
}
```
