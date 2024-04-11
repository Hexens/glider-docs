# Modifiers.instructions()

Returns Instructions object for the instructions of the modifiers.

## Return type

→ [Instructions](../instructions/)

An example to retrieve the instructions used by the modifiers with the name `onlyOwner` is as below

```python
from glider import *
def query():
  instructionlist = Modifiers()\
      .with_name("onlyOwner")\
      .instructions()\
      .exec(5)
  return instructionlist
```

## Output

```json
"root":{4 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"Ownable"
"sol_function":solidity
modifier onlyOwner() {
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
"sol_instruction":solidity
{
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
}
"root":{4 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"Ownable"
"sol_function":solidity
modifier onlyOwner() {
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
"sol_instruction":solidity
require(owner() == _msgSender(),"Ownable: caller is not the owner")
}
"root":{4 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"Ownable"
"sol_function":solidity
modifier onlyOwner() {
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
"sol_instruction":solidity
_
}
"root":{4 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"VRF_Pizza_RNG"
"sol_function":solidity
modifier onlyOwner() {
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
"sol_instruction":solidity
{
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
}
"root":{4 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"VRF_Pizza_RNG"
"sol_function":solidity
modifier onlyOwner() {
        require(owner() == _msgSender(),"Ownable: caller is not the owner");
        _;
    }
"sol_instruction":solidity
require(owner() == _msgSender(),"Ownable: caller is not the owner")
}

```
