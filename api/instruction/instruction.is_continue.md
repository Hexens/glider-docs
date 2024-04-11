---
description: >-
  Returns True if the instruction is CONTINUE instruction, otherwise returns
  False.
---

# Instruction.is\_continue()

Query

```python
from glider import *
def query():
  continues = []
  #fetch a list of instructions
  instructions = Instructions().exec(2750)
  for instruction in instructions:
    #check if instruction is a continue instruction
    if(instruction.is_continue()):
      continues.append(instruction)  
  return continues
```

Output

```
{
  "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
  "contract_name": "Vault",
  "sol_function": "function reclaimTokens(address to,address[] memory tokens) external nonReentrant {\n        require(_nft > 0,Exceptions.INITIALIZATION);\n        IProtocolGovernance governance = _vaultGovernance.internalParams().protocolGovernance;\n        bool isProtocolAdmin = governance.isAdmin(msg.sender);\n        require(isProtocolAdmin || _isApprovedOrOwner(msg.sender),Exceptions.ADMIN);\n        if (!isProtocolAdmin) {\n            require(_isValidPullDestination(to),Exceptions.VALID_PULL_DESTINATION);\n        }\n        uint256[] memory tokenAmounts = new uint256[](tokens.length);\n        for (uint256 i = 0; i < tokens.length; i++) {\n            IERC20 token = IERC20(tokens[i]);\n            tokenAmounts[i] = token.balanceOf(address(this));\n            if (tokenAmounts[i] == 0) {\n                continue;\n            }\n            token.safeTransfer(to,tokenAmounts[i]);\n        }\n        _postReclaimTokens(to,tokens);\n        emit ReclaimTokens(to,tokens,tokenAmounts);\n    }",
  "sol_instruction": "continue"
}
```
