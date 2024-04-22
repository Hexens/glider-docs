---
description: >-
  Returns Functions object for the functions that call the current node
  corresponding function.
---

# CallNode.caller\_functions()

```python
from glider import *

# task: find a function that has `burn*` call and return all the functions that has a call to that function

def query():
  data = []
  instructions = Instructions().with_called_function_name_prefix('burn').exec(10)
  for instruction in instructions:
    if len(data) > 0:
      break # demo first result only
    functionContainsBurn = instruction.get_parent() #api.functions.Function (*)
    contract = functionContainsBurn.get_contract() #api.contracts.Contract
    call_graph = contract.call_graph() #api.call_graph.CallGraph 
    nodes = call_graph.nodes() #Dict[str, CallNode]
    for id in nodes:
      if(id != functionContainsBurn.db_id):
        continue
      caller_functions = nodes[id].caller_functions #api.functions.Functions
      callers = caller_functions().exec() #List[Function]
      if len(callers) > 0:
        print(functionContainsBurn.source_code())
        for caller in callers:
          print(caller.source_code())
        data.append(instruction)
  return data
```

Output:

```json
{
  "print_output": [
    "function _beforeTokenTransfer(\n        address from,address to,uint256 amount\n    ) internal virtual override {\n        super._beforeTokenTransfer(from,to,amount);\n        \n        if (from == address(0) && to != address(0)) {\n            require(_erc20TokenAddress != address(0),\"_erc20TokenAddress must be defined\");\n            uint256 balanceOfAddress = IERC20(_erc20TokenAddress).balanceOf(to);\n            require(balanceOfAddress >= 1,\"user does not hold a token\");\n            ERC20Burnable(_erc20TokenAddress).burnFrom(to,1);\n        }\n    }",
    "function _mint(address to,uint256 tokenId) internal virtual {\n        require(to != address(0),\"ERC721: mint to the zero address\");\n        require(!_exists(tokenId),\"ERC721: token already minted\");\n\n        _beforeTokenTransfer(address(0),to,tokenId);\n\n        _balances[to] += 1;\n        _owners[tokenId] = to;\n\n        emit Transfer(address(0),to,tokenId);\n\n        _afterTokenTransfer(address(0),to,tokenId);\n    }",
    "function _burn(uint256 tokenId) internal virtual {\n        address owner = ERC721.ownerOf(tokenId);\n\n        _beforeTokenTransfer(owner,address(0),tokenId);\n\n        \n        _approve(address(0),tokenId);\n\n        _balances[owner] -= 1;\n        delete _owners[tokenId];\n\n        emit Transfer(owner,address(0),tokenId);\n\n        _afterTokenTransfer(owner,address(0),tokenId);\n    }",
    "function _transfer(\n        address from,address to,uint256 tokenId\n    ) internal virtual {\n        require(ERC721.ownerOf(tokenId) == from,\"ERC721: transfer from incorrect owner\");\n        require(to != address(0),\"ERC721: transfer to the zero address\");\n\n        _beforeTokenTransfer(from,to,tokenId);\n\n        \n        _approve(address(0),tokenId);\n\n        _balances[from] -= 1;\n        _balances[to] += 1;\n        _owners[tokenId] = to;\n\n        emit Transfer(from,to,tokenId);\n\n        _afterTokenTransfer(from,to,tokenId);\n    }"
  ]
}
```
