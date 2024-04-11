# Callables.with\_signature()

Adds a filter to get callables that have the given signature. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a list of signatures, refer to [Callables.with\_signatures()](callables.with\_signatures.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve all functions with the signature `transferFrom(address,address,uint256)`
  functions = Functions().with_signature("transferFrom(address,address,uint256)").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "IERC721",
        "sol_function": "function transferFrom(\n        address from,address to,uint256 tokenId\n    ) external;"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "IERC721Metadata",
        "sol_function": "function transferFrom(\n        address from,address to,uint256 tokenId\n    ) external;"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "ERC721",
        "sol_function": "function transferFrom(\n        address from,address to,uint256 tokenId\n    ) public virtual override {\n        \n        require(_isApprovedOrOwner(_msgSender(),tokenId),\"ERC721: transfer caller is not owner nor approved\");\n\n        _transfer(from,to,tokenId);\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "ERC721URIStorage",
        "sol_function": "function transferFrom(\n        address from,address to,uint256 tokenId\n    ) public virtual override {\n        \n        require(_isApprovedOrOwner(_msgSender(),tokenId),\"ERC721: transfer caller is not owner nor approved\");\n\n        _transfer(from,to,tokenId);\n    }"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP",
        "sol_function": "function transferFrom(\n        address from,address to,uint256 tokenId\n    ) public virtual override {\n        \n        require(_isApprovedOrOwner(_msgSender(),tokenId),\"ERC721: transfer caller is not owner nor approved\");\n\n        _transfer(from,to,tokenId);\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve all the modifiers with the signature `nonReentrant()`
  modifiers = Modifiers().with_signature("nonReentrant()").exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "ReentrancyGuard",
        "sol_modifier": "modifier nonReentrant() {\n        \n        require(_status != _ENTERED,\"ReentrancyGuard: reentrant call\");\n\n        \n        _status = _ENTERED;\n\n        _;\n\n        \n        \n        _status = _NOT_ENTERED;\n    }"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "StakingRewards",
        "sol_modifier": "modifier nonReentrant() {\n        \n        require(_status != _ENTERED,\"ReentrancyGuard: reentrant call\");\n\n        \n        _status = _ENTERED;\n\n        _;\n\n        \n        \n        _status = _NOT_ENTERED;\n    }"
    },
    {
        "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
        "contract_name": "ReentrancyGuard",
        "sol_modifier": "modifier nonReentrant() {\n        \n        require(_status != _ENTERED,\"ReentrancyGuard: reentrant call\");\n\n        \n        _status = _ENTERED;\n\n        _;\n\n        \n        \n        _status = _NOT_ENTERED;\n    }"
    },
    {
        "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
        "contract_name": "Vault",
        "sol_modifier": "modifier nonReentrant() {\n        \n        require(_status != _ENTERED,\"ReentrancyGuard: reentrant call\");\n\n        \n        _status = _ENTERED;\n\n        _;\n\n        \n        \n        _status = _NOT_ENTERED;\n    }"
    },
    {
        "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
        "contract_name": "GatewayVault",
        "sol_modifier": "modifier nonReentrant() {\n        \n        require(_status != _ENTERED,\"ReentrancyGuard: reentrant call\");\n\n        \n        _status = _ENTERED;\n\n        _;\n\n        \n        \n        _status = _NOT_ENTERED;\n    }"
    }
]
```
