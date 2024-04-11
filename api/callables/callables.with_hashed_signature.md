# Callables.with\_hashed\_signature()

Adds a filter to get callables having specified selector. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have 0x70a08231 as selector
  functions = Functions().with_hashed_signature(0x70a08231).exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "IERC721",
        "sol_function": "function balanceOf(address owner) external view returns (uint256 balance);"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "IERC721Metadata",
        "sol_function": "function balanceOf(address owner) external view returns (uint256 balance);"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "ERC721",
        "sol_function": "function balanceOf(address owner) public view virtual override returns (uint256) {\n        require(owner != address(0),\"ERC721: balance query for the zero address\");\n        return _balances[owner];\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "ERC721URIStorage",
        "sol_function": "function balanceOf(address owner) public view virtual override returns (uint256) {\n        require(owner != address(0),\"ERC721: balance query for the zero address\");\n        return _balances[owner];\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP",
        "sol_function": "function balanceOf(address owner) public view virtual override returns (uint256) {\n        require(owner != address(0),\"ERC721: balance query for the zero address\");\n        return _balances[owner];\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have 0x2ddb862d as their selector
  modifiers = Modifiers().with_hashed_signature(0x2ddb862d).exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP",
        "sol_modifier": "modifier onlyMinter() {\n        require(msg.sender == minter,'Sender is not the minter');\n        _;\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "CoreRef",
        "sol_modifier": "modifier onlyMinter() {\n        require(_core.isMinter(msg.sender),\"CoreRef: Caller is not a minter\");\n        _;\n    }"
    },
    {
        "contract": "0x1d8B9d1334575b5cB265E63D2A5AD0E70Fe46A2B",
        "contract_name": "Rusd",
        "sol_modifier": "modifier onlyMinter() {\n        require(_core.isMinter(msg.sender),\"CoreRef: Caller is not a minter\");\n        _;\n    }"
    },
    {
        "contract": "0x36b367EC5f063605b0f8457383DA38E691E1c559",
        "contract_name": "suDAO",
        "sol_modifier": "modifier onlyMinter() {\n        require(isMinter[msg.sender] || (msg.sender == owner()),\"caller is not a minter\");\n        _;\n    }"
    },
    {
        "contract": "0xe472c2b246177E15f18Cf9AC72339A8ed965e5DA",
        "contract_name": "MinterRole",
        "sol_modifier": "modifier onlyMinter() {\n        require(isMinter(_msgSender()),\"MinterRole: caller does not have the Minter role\");\n        _;\n    }"
    }
]
```
