# Functions.with\_one\_of\_the\_modifier\_name\_regexes()

`with_one_of_the_modifier_name_regexes(`_`regexes: List[str]`_`) →` [`Functions`](./)

Adds a filter to get functions that have a modifier whose name matches one of the given regexes.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions with modifiers matching regex list
  functions = Functions().with_one_of_the_modifier_name_regexes(['^only.*', 'admin']).exec(10)

  return functions
```

## Output

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "function renounceOwnership() public virtual onlyOwner {\n        _setOwner(address(0));\n    }"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Ownable",
    "sol_function": "function transferOwnership(address newOwner) public virtual onlyOwner {\n        require(newOwner != address(0),\"Ownable: new owner is the zero address\");\n        _setOwner(newOwner);\n    }"
  }
]
</code></pre>
