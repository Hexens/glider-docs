# Functions.with\_modifier\_name\_regex()

Adds a filter to get functions, that have modifier whose name matches the given regex.

Parameters : `regex: str`

```python
from glider import *

def query():
  
  # Fetch a list of functions with modifiers starting with 'only'
  functions = Functions().with_modifier_name_regex('^only.*').exec(10)

  return functions
```

\


Output:

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "function renounceOwnership() public virtual onlyOwner {\n        _setOwner(address(0));\n    }"
    },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "LTP",
    "sol_function": "function issueNft(address to,uint256 tokenId,uint256 amount,string memory tokenURI) external payable onlyMinterOrOwner { \n        \n        require(to != address(this),\"Issue to a new address\");\n        require(ownerOf(tokenId) == address(this),\"NFT already issued\");\n        \n        \n\n        _setTokenURI(nextId,tokenURI);\n        this.safeTransferFrom(address(this),to,tokenId);\n        emit NFTIssued(tokenId,to,tokenURI);\n    }"
  }
]
</code></pre>
