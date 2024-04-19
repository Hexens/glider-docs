# Call.get\_args()

`get_args() → List[`[`Value`](../value/)`]`



## Query Example

```python
from glider import *

def query():
  instructions = (
    Contracts().
    non_interface_contracts().
    functions().
    instructions().
    exec(1,2)
  )

  output = []

  for entry_ins in instructions:
    for next_ins in entry_ins.next_instructions():
      for operand in next_ins.get_operands():
        if isinstance(operand, Call):
          output.append(next_ins)
          for arg in operand.get_args():
            print(arg, arg.expression)

  return output
```

## Output Example

```solidity
{
    "contract":"0xd705c24267ed3c55458160104994c55c6492dfcf"
    "contract_name":"SafeMath"
    "sol_function":
        function add(uint256 a, uint256 b) internal pure returns (uint256) {
            uint256 c = a + b;
            require(c >= a, "SafeMath: addition overflow");
            return c;
        }
    "sol_instruction":
        require(c >= a, "SafeMath: addition overflow")
},
{
    "print_output":[
        0: "<api.value.ConditionalExpression object at 0x7fc5d4959c10>"
        1: "c >= a"
        2: "<api.value.Literal object at 0x7fc5d495a910>"
        3: "SafeMath: addition overflow"
    ]
}
```
