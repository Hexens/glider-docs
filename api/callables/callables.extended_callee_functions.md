---
description: >-
  Returns a Functions object representing the functions which are called from
  the callables of the Callables object.
---

# Callables.extended\_callee\_functions()

`extended_callee_functions() →` [`Functions`](functions/)

## Query Example

```python
from glider import *

def query():
  functions = Functions().with_name("transferFrom").exec(10)

  callee_functions = []
  for func in functions:
    for callee_func in func.extended_callee_functions().exec():
      callee_functions.append(callee_func)

  return callee_functions
```

## Output Example

```solidity
[
  {
    "contract": "0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "contract_name": "RetroDoge",
    "contract_link": "https://etherscan.io/address/0xeb42dce76e77818638c5f6be2cb1f6906d52e5d2",
    "uuid": "65e74ade-7cc7-45f1-91d8-9616d2c02513",
    "severity": "",
    "sol_function": 
    function _transfer(
      address from,
      address to,
      uint256 tokenId
    ) private {
      TokenOwnership memory prevOwnership = _ownershipOf(tokenId);
      
      if (prevOwnership.addr != from) revert TransferFromIncorrectOwner();
      
      bool isApprovedOrOwner = (_msgSender() == from ||
        isApprovedForAll(from, _msgSender()) ||
        getApproved(tokenId) == _msgSender());
        
      if (!isApprovedOrOwner) revert TransferCallerNotOwnerNorApproved();
      if (to == address(0)) revert TransferToZeroAddress();
      
      _beforeTokenTransfers(from, to, tokenId, 1);
      
      // Clear approvals from the previous owner
      _approve(address(0), tokenId, from);
      
      // Underflow of the sender's balance is impossible because we check for
      // ownership above and the recipient's balance can't realistically overflow.
      // Counter overflow is incredibly unrealistic as tokenId would have to be 2**256.
      unchecked {
        _addressData[from].balance -= 1;
        _addressData[to].balance += 1;
        
        TokenOwnership storage currSlot = _ownerships[tokenId];
        currSlot.addr = to;
        currSlot.startTimestamp = uint64(block.timestamp);
        
        // If the ownership slot of tokenId+1 is not explicitly set, that means the transfer initiator owns it.
        // Set the slot of tokenId+1 explicitly in storage to maintain correctness for ownerOf(tokenId+1) calls.
        uint256 nextTokenId = tokenId + 1;
        TokenOwnership storage nextSlot = _ownerships[nextTokenId];
        if (nextSlot.addr == address(0)) {
          // This will suffice for checking _exists(nextTokenId),
          // as a burned slot cannot contain the zero address.
          if (nextTokenId != _currentIndex) {
            nextSlot.addr = from;
            nextSlot.startTimestamp = prevOwnership.startTimestamp;
          }
        }
      }
      
      emit Transfer(from, to, tokenId);
      _afterTokenTransfers(from, to, tokenId, 1);
    }
  },
  ... 
]
```
