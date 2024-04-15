---
description: Returns the calls used in the instruction
---

# Instruction.get\_callee\_values()

`get_callee_values() → List[Call]`

The function returns an array of Call objects representing calls that are used in the instruction.

For example, in the instruction:

```solidity
return keccak256(abi.encodePacked(account , amount));
```

The function will return Call objects for keccak256 and abi.encodePacked calls.

## Query Example

```python
from glider import *
def query():
  #fetch an instruction
  instruction = Instructions().with_all_callee_function_names(['keccak256','abi.encodePacked']).exec(1)
  #print the expression of the callee
  for call in instruction[0].get_callee_values():
    print(call.expression)
  return instruction
```

## Output

```solidity
"root":{4 items
"contract":string"0x8a93bc8ed29da1b090265137a9d201ebf1154626"
"contract_name":string"METAANIxKPP"
"sol_function":solidity
function _leaf(address account, uint256 amount)
    internal pure returns (bytes32)
    {
        return keccak256(abi.encodePacked(account , amount));
    }
"sol_instruction":solidity
return keccak256(abi.encodePacked(account , amount))
},
"root":{1 item
    "print_output":[2 items
    0:string"keccak256(bytes)(abi.encodePacked(account,amount))"
    1:string"abi.encodePacked(account,amount)"
    ]
}
```
