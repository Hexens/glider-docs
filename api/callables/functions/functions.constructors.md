# Functions.constructors()

`constructors() →` [`Functions`](./)

Adds a filter to get only the constructors.

## Example

```python
from glider import *

def query():
  # Fetch a list of constructors
  functions = Functions().constructors().exec(2)

  return functions
```

## Output

<pre class="language-json"><code class="lang-json"><strong>[
</strong><strong>  {
</strong>    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "constructor() {\n        _setOwner(_msgSender());\n    }"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "ERC721",
    "sol_function": "constructor(string memory name_,string memory symbol_) {\n        _name = name_;\n        _symbol = symbol_;\n    }"
  }
]
</code></pre>

## Old constructor syntax

The function also accounts for the old constructor syntax, which in the older Solidity versions was named the same as the contract.&#x20;

```python
from glider import *

def query():
  funcs = Functions().constructors().without_name('constructor').exec(2)
  return funcs
```

Output

```solidity
"root":{3 items
"contract":string"0x1cfa0b95c531bc2c88a81a4263f6a6f5c1613b96"
"contract_name":string"owned"
"sol_function":solidity
function owned() public {
        owner = msg.sender;
    }
},
"root":{3 items
"contract":string"0x1cfa0b95c531bc2c88a81a4263f6a6f5c1613b96"
"contract_name":string"TokenERC20"
"sol_function":solidity
function TokenERC20(
        uint256 initialSupply,
        string tokenName,
        string tokenSymbol
    ) public {
        totalSupply = initialSupply * 10 ** uint256(decimals);  // Update total supply with the decimal amount
        balanceOf[msg.sender] = totalSupply;                // Give the creator all initial tokens
        name = tokenName;                                   // Set the name for display purposes
        symbol = tokenSymbol;                               // Set the symbol for display purposes
    }
}

```

