---
description: >-
  with_all_properties is deprecated and will be removed in future versions.
  Please use with_properties in- stead. Adds a filter to get functions that have
  all given properties.
---

# Functions.with\_all\_properties()

**Deprecated:** This method is deprecated and will be removed in future versions.

**Alternative:** Use `with_properties()` instead for improved functionality.

`with_all_properties(`_`properties: List[`_[_`MethodProp`_](../methodprop/)_`]`_`) →` [`Functions`](./)

## Example

```python
from glider import *

def query():
  properties = [MethodProp.IS_PAYABLE, MethodProp.EXTERNAL]
  # Fetch a list of functions with all the properties
  functions = Functions().with_all_properties(properties).exec(10)

  return functions
```

## Output

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
