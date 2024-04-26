# Modifiers.placer\_instructions()

`placer_instructions() →` [`Instructions`](../../instructions/)

Returns placeholder [instructions](../../instructions/) for the set of [Modifiers](./).

The placeholder or placer instruction is the "\_" (underline) instruction which defines where the function code must be inline in the modifier.

## Return type

→ [Instructions](../../instructions/)

An example to retrieve the instructions used by the modifiers with the name `onlyOwner` is as below

```python
from glider import *
def query():
  instructionlist = Modifiers()\
      .with_name("onlyOwner")\
      .placer_instructions()\
      .exec(5)
  return instructionlist
```

## Output

```solidity
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
