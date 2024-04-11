# Contract.source\_code()

## Description

Returns the source code of the contract.

## Return type

str

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(2)
  
  codes = []
  for contract in contracts:
    code = contract.source_code()
    codes.append(code)

  return [{"codes": codes}]
```

## Example output

```json
{
  "codes": [
    "abstract contract Context {\n    function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }\n\n    function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }\n}",
    "abstract contract Ownable is Context {\n    address private _owner;\n\n    event OwnershipTransferred(address indexed previousOwner,address indexed newOwner);\n\n    \n\n\n    constructor() {\n        _setOwner(_msgSender());\n    }\n\n    \n\n\n    function owner() public view virtual returns (address) {\n        return _owner;\n    }\n\n    \n\n\n    modifier onlyOwner() {\n        require(owner() == _msgSender(),\"Ownable: caller is not the owner\");\n        _;\n    }\n\n    \n\n\n\n\n\n\n    function renounceOwnership() public virtual onlyOwner {\n        _setOwner(address(0));\n    }\n\n    \n\n\n\n    function transferOwnership(address newOwner) public virtual onlyOwner {\n        require(newOwner != address(0),\"Ownable: new owner is the zero address\");\n        _setOwner(newOwner);\n    }\n\n    function _setOwner(address newOwner) private {\n        address oldOwner = _owner;\n        _owner = newOwner;\n        emit OwnershipTransferred(oldOwner,newOwner);\n    }\n}"
  ]
}
```
