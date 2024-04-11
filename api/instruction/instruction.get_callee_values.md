# Instruction.get\_callee\_values()



Query

```python
from glider import *
def query():
  #fetch an instruction
  instruction = Instructions().exec(1,16)
  #print the expression of the callee
  print(instruction[0].get_callee_values()[0].expression) 
  return []
```

Output

```json
{
    "print_output": 
        ["require(bool,string)(newOwner != address(0),\"Ownable: new owner is the zero address\")"]
}
```
