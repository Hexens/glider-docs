# Contract.get\_contracts\_from\_same\_src\_file()

## Description

Returns a collection of lists, with each list representing contracts originating from the same document.

## Return type

List\[List\[[Contract](./)]]

## Example query

```python
from glider import *

def query():
  contracts = Contracts().exec(1)
  
  first_file_names = []
  second_file_names = []
  for contract in contracts:
    same_files_contracts = contract.get_contracts_from_same_src_file()
    first_file_contracts = same_files_contracts[0]
    second_file_contracts = same_files_contracts[1]

    for contract in first_file_contracts:
      first_file_names.append(contract.name)
      
    for contract in second_file_contracts:
      second_file_names.append(contract.name)

  return [{"first_file_names": first_file_names, "second_file_names": second_file_names}]
```

## Example output

```json
{
  "first_file_names": [
    "Context",
    "Ownable",
    "IERC165",
    "ERC165",
    "IERC721",
    "IERC721Metadata",
    "ERC721",
    "ERC721URIStorage",
    "ISuperApp",
    "SuperAppBase",
    "LTP",
    "ISuperAgreement",
    "IConstantFlowAgreementV1",
    "IERC721Receiver",
    "Address",
    "Strings",
    "ISuperfluid",
    "ISuperfluidGovernance",
    "ISuperfluidToken",
    "TokenInfo",
    "IERC20",
    "IERC777",
    "ISuperToken",
    "ISuperTokenFactory",
    "SuperAppDefinitions",
    "ContextDefinitions",
    "BatchOperation",
    "SuperfluidGovernanceConfigs",
    "ERC20WithTokenInfo"
  ],
  "second_file_names": [
    "IERC20",
    "IERC20Metadata",
    "Context",
    "ERC20",
    "Ownable",
    "INodeERC1155",
    "ICorkToken",
    "CorkToken"
  ]
}
```
