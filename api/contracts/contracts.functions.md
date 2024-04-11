---
description: Returns the Functions object for the functions of the contracts.
---

# Contracts.functions()

Input:

```python
from glider import *

def query():
  contracts = Contracts().functions().exec(5)

  return contracts
```

Output:

```python
"root":{3 items
"contract":string"0x82e3077da0d038197b810d0620aed3e513164694"
"contract_name":string"Voting"
"sol_function":solidity
function isWhitelisted(address addr) public view returns (bool) {
        return whitelist[addr]!=0;
    }
}
"root":{3 items
"contract":string"0x82e3077da0d038197b810d0620aed3e513164694"
"contract_name":string"Voting"
"sol_function":solidity
function whitelistAddress(address addr) public onlyOwner{
        require(!isWhitelisted(addr),"Already whitelisted");
        counter++;
        _voters++;
        whitelist[addr]=counter;
    }
}
"root":{3 items
"contract":string"0x82e3077da0d038197b810d0620aed3e513164694"
"contract_name":string"Voting"
"sol_function":solidity
function removeAddress(address addr) public onlyOwner{
        require(isWhitelisted(addr),"Not whitelisted");
        _voters--;
        whitelist[addr] = 0;
    }
}
"root":{3 items
"contract":string"0x82e3077da0d038197b810d0620aed3e513164694"
"contract_name":string"Voting"
"sol_function":solidity
function numVoters() public view returns (uint){
        return _voters;
    }
}
"root":{3 items
"contract":string"0x82e3077da0d038197b810d0620aed3e513164694"
"contract_name":string"Voting"
"sol_function":solidity
function addProposer(address addr) public onlyOwner{
        isProposer[addr]=true;
    }
}
```
