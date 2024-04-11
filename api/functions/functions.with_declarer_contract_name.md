# Functions.with\_declarer\_contract\_name()

Adds a filter to get functions that have declarer contract with the given name.

Parameters : `name: str, sensitivity: bool = True`

```python
from glider import *

def query():
  
  # Fetch a list of functions with declarer contract name 'Vault'
  functions = Functions().with_declarer_contract_name('Vault').exec(10)

  return functions
```

\


Output:

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
    "contract_name": "Vault",
    "sol_function": "constructor(IVaultGovernance vaultGovernance_,address[] memory vaultTokens_) {\n        require(CommonLibrary.isSortedAndUnique(vaultTokens_),Exceptions.SORTED_AND_UNIQUE);\n        _vaultGovernance = vaultGovernance_;\n        _vaultTokens = vaultTokens_;\n        for (uint256 i = 0; i &#x3C; vaultTokens_.length; i++) {\n            _vaultTokensIndex[vaultTokens_[i]] = true;\n        }\n    }"
  },
  {
    "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
    "contract_name": "Vault",
    "sol_function": "function vaultGovernance() external view returns (IVaultGovernance) {\n        return _vaultGovernance;\n    }"
  }
]
</code></pre>
