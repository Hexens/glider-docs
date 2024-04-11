---
description: Returns corresponding function.
---

# CallNode.function()

```python
from glider import *

# find a contract with name UnistakeToken and print source code of all the functions
def query():
  contracts = Contracts().name_regex("UnistakeToken").exec(5)
  for contract in contracts:
    call_graph = contract.call_graph() #api.call_graph.CallGraph instance 
    nodes = call_graph.nodes() #api.call_graph.CallNode instance
    for id in nodes:
      fn = nodes[id].function() #api.functions.Function instance
      print(fn.source_code()) #api.functions.Callable instance (base class of api.functions.Function)
  return contracts
```

Output:

```json
{
  "print_output": [
    "function burn(uint256 amount) public virtual {\n        _burn(_msgSender(),amount);\n    }",
    "function burnFrom(address account,uint256 amount) public virtual {\n        _spendAllowance(account,_msgSender(),amount);\n        _burn(account,amount);\n    }",
    "constructor(string memory name_,string memory symbol_) {\n        _name = name_;\n        _symbol = symbol_;\n    }",
    "function name() public view virtual override returns (string memory) {\n        return _name;\n    }",
    "function symbol() public view virtual override returns (string memory) {\n        return _symbol;\n    }",
    "function decimals() public view virtual override returns (uint8) {\n        return 18;\n    }",
    "function totalSupply() public view virtual override returns (uint256) {\n        return _totalSupply;\n    }",
    "function balanceOf(address account) public view virtual override returns (uint256) {\n        return _balances[account];\n    }",
    "function transfer(address to,uint256 amount) public virtual override returns (bool) {\n        address owner = _msgSender();\n        _transfer(owner,to,amount);\n        return true;\n    }",
    "function allowance(address owner,address spender) public view virtual override returns (uint256) {\n        return _allowances[owner][spender];\n    }",
    "function approve(address spender,uint256 amount) public virtual override returns (bool) {\n        address owner = _msgSender();\n        _approve(owner,spender,amount);\n        return true;\n    }",
    "function transferFrom(\n        address from,address to,uint256 amount\n    ) public virtual override returns (bool) {\n        address spender = _msgSender();\n        _spendAllowance(from,spender,amount);\n        _transfer(from,to,amount);\n        return true;\n    }",
    "function increaseAllowance(address spender,uint256 addedValue) public virtual returns (bool) {\n        address owner = _msgSender();\n        _approve(owner,spender,allowance(owner,spender) + addedValue);\n        return true;\n    }",
    "function decreaseAllowance(address spender,uint256 subtractedValue) public virtual returns (bool) {\n        address owner = _msgSender();\n        uint256 currentAllowance = allowance(owner,spender);\n        require(currentAllowance >= subtractedValue,\"ERC20: decreased allowance below zero\");\n        unchecked {\n            _approve(owner,spender,currentAllowance - subtractedValue);\n        }\n\n        return true;\n    }",
    "function _transfer(\n        address from,address to,uint256 amount\n    ) internal virtual {\n        require(from != address(0),\"ERC20: transfer from the zero address\");\n        require(to != address(0),\"ERC20: transfer to the zero address\");\n\n        _beforeTokenTransfer(from,to,amount);\n\n        uint256 fromBalance = _balances[from];\n        require(fromBalance >= amount,\"ERC20: transfer amount exceeds balance\");\n        unchecked {\n            _balances[from] = fromBalance - amount;\n        }\n        _balances[to] += amount;\n\n        emit Transfer(from,to,amount);\n\n        _afterTokenTransfer(from,to,amount);\n    }",
    "function _mint(address account,uint256 amount) internal virtual {\n        require(account != address(0),\"ERC20: mint to the zero address\");\n\n        _beforeTokenTransfer(address(0),account,amount);\n\n        _totalSupply += amount;\n        _balances[account] += amount;\n        emit Transfer(address(0),account,amount);\n\n        _afterTokenTransfer(address(0),account,amount);\n    }",
    "function _burn(address account,uint256 amount) internal virtual {\n        require(account != address(0),\"ERC20: burn from the zero address\");\n\n        _beforeTokenTransfer(account,address(0),amount);\n\n        uint256 accountBalance = _balances[account];\n        require(accountBalance >= amount,\"ERC20: burn amount exceeds balance\");\n        unchecked {\n            _balances[account] = accountBalance - amount;\n        }\n        _totalSupply -= amount;\n\n        emit Transfer(account,address(0),amount);\n\n        _afterTokenTransfer(account,address(0),amount);\n    }",
    "function _approve(\n        address owner,address spender,uint256 amount\n    ) internal virtual {\n        require(owner != address(0),\"ERC20: approve from the zero address\");\n        require(spender != address(0),\"ERC20: approve to the zero address\");\n\n        _allowances[owner][spender] = amount;\n        emit Approval(owner,spender,amount);\n    }",
    "function _spendAllowance(\n        address owner,address spender,uint256 amount\n    ) internal virtual {\n        uint256 currentAllowance = allowance(owner,spender);\n        if (currentAllowance != type(uint256).max) {\n            require(currentAllowance >= amount,\"ERC20: insufficient allowance\");\n            unchecked {\n                _approve(owner,spender,currentAllowance - amount);\n            }\n        }\n    }",
    "function _beforeTokenTransfer(\n        address from,address to,uint256 amount\n    ) internal virtual {}",
    "function _afterTokenTransfer(\n        address from,address to,uint256 amount\n    ) internal virtual {}",
    "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }",
    "function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }",
    "constructor() ERC20(\"Unistake Token\",\"UNISTAKE\") {\n        _mint(msg.sender,280000000 * 10**18);\n    }"
  ]
}
```
