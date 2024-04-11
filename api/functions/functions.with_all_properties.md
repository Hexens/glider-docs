# Functions.with\_all\_properties()

Adds a filter to get functions that have all given properties.

Parameters : `properties: List[MethodProp]`

```python
from glider import *

def query():

  properties = [MethodProp.IS_PAYABLE, MethodProp.EXTERNAL]
  
  # Fetch a list of functions with all the properties
  functions = Functions().with_all_properties(properties).exec(10)

  return functions
```

\


Output:

<pre class="language-json"><code class="lang-json"><strong>[
</strong><strong>  {
</strong>    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "LTP",
    "sol_function": "function issueNft(address to,uint256 tokenId,uint256 amount,string memory tokenURI) external payable onlyMinterOrOwner { \n        \n        require(to != address(this),\"Issue to a new address\");\n        require(ownerOf(tokenId) == address(this),\"NFT already issued\");\n        \n        \n\n        _setTokenURI(nextId,tokenURI);\n        this.safeTransferFrom(address(this),to,tokenId);\n        emit NFTIssued(tokenId,to,tokenURI);\n    }"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "LTP",
    "sol_function": "function withdrawETH() external payable onlyOwner {\n        payable(msg.sender).transfer(address(this).balance);\n    }"
  }
]
</code></pre>
