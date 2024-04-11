---
description: Returns continue instructions of the function/modifier.
---

# Callable.continue\_instructions()

## Return type

→ [Instructions](../instructions/)

## Example

```python
from glider import *
def query():
  functions = Functions().exec(100)

  continue_instructions = []
  for function in functions:
    # List all continue instructions inside the given functions
    for instruction in function.continue_instructions().exec():
      continue_instructions.append(instruction)

  return continue_instructions
```

## Example output

```json
[
  {
    "contract": "0x31Cef25171d9b06B6A8eF9dEBBFCf84c9aaB5A32",
    "contract_name": "Vault",
    // Formatted for the example
    "sol_function": `
    function reclaimTokens(address to,address[] memory tokens) external {
        IProtocolGovernance governance = _vaultGovernance.internalParams().protocolGovernance;
        bool isProtocolAdmin = governance.isAdmin(msg.sender);
        require(isProtocolAdmin || _isApprovedOrOwner(msg.sender),"ADM");
        if (!isProtocolAdmin) {
            require(_isValidPullDestination(to),"INTRA");
        }
        
        uint256[] memory tokenAmounts = new uint256[](tokens.length);
        
        for (uint256 i = 0; i < tokens.length; i++) {
            IERC20 token = IERC20(tokens[i]);
            tokenAmounts[i] = token.balanceOf(address(this));
            if (tokenAmounts[i] == 0) {
                continue;
            }
            token.safeTransfer(to,tokenAmounts[i]);
        }
        
        _postReclaimTokens(to,tokens);
        emit ReclaimTokens(to,tokens,tokenAmounts);
    }
    `,
    "sol_instruction": "continue"
  },
  ...
]
```
