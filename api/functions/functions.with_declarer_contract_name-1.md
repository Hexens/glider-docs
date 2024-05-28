---
description: >-
  Adds a filter to get functions that have declarer contract with the given
  name.
---

# Functions.with\_declarer\_contract\_name()

The function adds a filter for the functions to be declared in a contract with a specific name.

## Example

```python
from glider import *

def query():
	# lets say we want to take transferFrom functions, but only from ERC721 contracts and not ERC20
    functions = Functions()\
        .with_name('transferFrom')\
        .with_declarer_contract_name('ERC721')\
        .exec(3)

    return functions
```

## Example Output

```solidity
"root":{3 items
"contract":string"0x6b7be5a6d0d432ae4e597f062fdefb021b535298"
"contract_name":string"ERC721"
"sol_function":solidity
function transferFrom(
        address from,
        address to,
        uint256 tokenId
    ) public virtual override {
        //solhint-disable-next-line max-line-length
        require(_isApprovedOrOwner(_msgSender(), tokenId), "ERC721: transfer caller is not owner nor approved");

        _transfer(from, to, tokenId);
    }
}
"root":{3 items
"contract":string"0x6b7be5a6d0d432ae4e597f062fdefb021b535298"
"contract_name":string"ERC721URIStorage"
"sol_function":solidity
function transferFrom(
        address from,
        address to,
        uint256 tokenId
    ) public virtual override {
        //solhint-disable-next-line max-line-length
        require(_isApprovedOrOwner(_msgSender(), tokenId), "ERC721: transfer caller is not owner nor approved");

        _transfer(from, to, tokenId);
    }
}
"root":{3 items
"contract":string"0x6b7be5a6d0d432ae4e597f062fdefb021b535298"
"contract_name":string"TimeSyncNFT"
"sol_function":solidity
function transferFrom(
        address from,
        address to,
        uint256 tokenId
    ) public virtual override {
        //solhint-disable-next-line max-line-length
        require(_isApprovedOrOwner(_msgSender(), tokenId), "ERC721: transfer caller is not owner nor approved");

        _transfer(from, to, tokenId);
    }
}
```



{% hint style="info" %}
As can be seen, the output consists of the same function deployed under the same address but with different contract names, two of which are not ERC721. In fact, the query worked correctly, and the last two functions are included in the result as the function that is declared in ERC721 is, in fact, being inherited by those contracts.
{% endhint %}
