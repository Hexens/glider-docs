# Callables.name\_regex()

Adds a filter to get callables whose names match the given regex expression. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

To filter given a list of regex expression, refer to [Callables.name\_regexes()](callables.name\_regexes.md).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the functions that have `claim` in their name but do not start with `_`
  functions = Functions().name_regex(r"^(?!_).*claim.*$").exec(100)

  # Return the first five functions
  return functions[0:5]
```

Output:

```json
[
    {
        "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
        "contract_name": "IVault",
        "sol_function": "function reclaimTokens(address to,address[] memory tokens) external;"
    },
    {
        "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
        "contract_name": "IVault",
        "sol_function": "function claimRewards(address from,bytes memory data) external;"
    },
    {
        "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
        "contract_name": "IGatewayVault",
        "sol_function": "function reclaimTokens(address to,address[] memory tokens) external;"
    },
    {
        "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
        "contract_name": "IGatewayVault",
        "sol_function": "function claimRewards(address from,bytes memory data) external;"
    },
    {
        "contract": "0x5C3975C1F017833156806435cF123F8Cb0651F5f",
        "contract_name": "Vault",
        "sol_function": "function reclaimTokens(address to,address[] memory tokens) external nonReentrant {\n        require(_nft > 0,Exceptions.INITIALIZATION);\n        IProtocolGovernance governance = _vaultGovernance.internalParams().protocolGovernance;\n        bool isProtocolAdmin = governance.isAdmin(msg.sender);\n        require(isProtocolAdmin || _isApprovedOrOwner(msg.sender),Exceptions.ADMIN);\n        if (!isProtocolAdmin) {\n            require(_isValidPullDestination(to),Exceptions.VALID_PULL_DESTINATION);\n        }\n        uint256[] memory tokenAmounts = new uint256[](tokens.length);\n        for (uint256 i = 0; i < tokens.length; i++) {\n            IERC20 token = IERC20(tokens[i]);\n            tokenAmounts[i] = token.balanceOf(address(this));\n            if (tokenAmounts[i] == 0) {\n                continue;\n            }\n            token.safeTransfer(to,tokenAmounts[i]);\n        }\n        _postReclaimTokens(to,tokens);\n        emit ReclaimTokens(to,tokens,tokenAmounts);\n    }"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the modifiers that have `claim` in their name but do not start with `only`
  modifiers = Modifiers().name_regex(r"^(?!only).*claim.*$").exec(100)

  # Return the first five modifiers
  return modifiers[0:5]
```

Output:

```json
[
    {
        "contract": "0x99DAFE76a1A3E94A0850Ee7CDFf51e2050522c75",
        "contract_name": "AirDrop",
        "sol_modifier": "modifier claimActive() {\n    require(_claimActivated == true,\"AIRDROP: Claim has not been activated!\");\n    require(_endContest > 0 && block.timestamp < _endContest ,\"AIRDROP: Claim has not been activated!\");\n\n    _;\n  }"
    },
    {
        "contract": "0x99DAFE76a1A3E94A0850Ee7CDFf51e2050522c75",
        "contract_name": "AirDrop",
        "sol_modifier": "modifier claimNotActive() {\n    require(_claimActivated == false,\"AIRDROP: Claim has been activated!\");\n    require(_endContest < block.timestamp,\"AIRDROP: Claim has been expired!\");\n\n    _;\n  }"
    },
    {
        "contract": "0xB87B56D17Fd0777e270BAECeaB6C678fa1b93971",
        "contract_name": "AirDrop",
        "sol_modifier": "modifier claimActive() {\n    require(_claimActivated == true,\"AIRDROP: Claim has not been activated!\");\n    require(_endContest > 0 && block.timestamp < _endContest ,\"AIRDROP: Claim has not been activated!\");\n\n    _;\n  }"
    },
    {
        "contract": "0xB87B56D17Fd0777e270BAECeaB6C678fa1b93971",
        "contract_name": "AirDrop",
        "sol_modifier": "modifier claimNotActive() {\n    require(_claimActivated == false,\"AIRDROP: Claim has been activated!\");\n    require(_endContest < block.timestamp,\"AIRDROP: Claim has been expired!\");\n\n    _;\n  }"
    },
    {
        "contract": "0x04aff94C91c11B5dF7298633a614Dbe7673796D9",
        "contract_name": "AirDrop",
        "sol_modifier": "modifier claimActive() {\n    require(_claimActivated == true,\"AIRDROP: Claim has not been activated!\");\n    require(_endContest > 0 && block.timestamp < _endContest ,\"AIRDROP: Claim has not been activated!\");\n\n    _;\n  }"
    }
]
```
