# Functions.with\_modifier\_name()

Adds a filter to get functions that have a modifier with the given name.

Parameters : `name: str, sensitivity: bool = True`

```python
from glider import *

def query():
  
  # Fetch a list of functions with nonReentrant modifier
  functions = Functions().with_modifier_name('nonReentrant').exec(10)

  return functions
```

\


Output:

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
    "contract_name": "StakingRewards",
    "sol_function": "function stake(uint256 amount) external nonReentrant notPaused updateReward(msg.sender) {\n        require(amount > 0,\"Cannot stake 0\");\n        _totalSupply = _totalSupply.add(amount);\n        _balances[msg.sender] = _balances[msg.sender].add(amount);\n        stakingToken.safeTransferFrom(msg.sender,address(this),amount);\n        emit Staked(msg.sender,amount);\n    }"
  },
  {
    "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
    "contract_name": "StakingRewards",
    "sol_function": "function withdraw(uint256 amount) public nonReentrant updateReward(msg.sender) {\n        require(amount > 0,\"Cannot withdraw 0\");\n        _totalSupply = _totalSupply.sub(amount);\n        _balances[msg.sender] = _balances[msg.sender].sub(amount);\n        stakingToken.safeTransfer(msg.sender,amount);\n        emit Withdrawn(msg.sender,amount);\n    }"
  }
]
</code></pre>
