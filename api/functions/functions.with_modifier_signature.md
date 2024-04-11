# Functions.with\_modifier\_signature()

Adds a filter to get functions that have a modifier with the given signature.

Parameters : `signature: str`

```python
from glider import *

def query():
  
  # Fetch a list of functions with specific modifier signature
  functions = Functions().with_modifier_signature('onlyOwner(address)').exec(10)

  return functions
```

\


Output:

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "contract": "0x4D0Ef64d92e681840CCd929391D1B8CD3B175FA6",
    "contract_name": "PiggyBankFundraise",
    "sol_function": "function disburseFunds(address _client) public onlyOwner(_client) {\n        require(!fundsWithdrawn,\"fund withdraw has already been called\");\n        require(checkFundraisingTarget()==true,\"funding goal not met\");\n        \n        fundsWithdrawn = true;\n        emit WithdrawAll(address(this).balance,block.timestamp);\n        owner.transfer(address(this).balance);\n    }"
  },
  {
    "contract": "0xFBb2bE4d126D4B4478d2416D59268101DF633E5e",
    "contract_name": "UserSharesInfo",
    "sol_function": "function forwardAddress(address addr,address newAddr) \n        public onlyOwner(addr) {\n        \n        addressForwards[addr] = newAddr;\n    }"
  }
]
</code></pre>
