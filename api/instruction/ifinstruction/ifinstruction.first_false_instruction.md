# IfInstruction.first\_false\_instruction()

`first_false_instruction() →` [`Instruction`](../)

The function returns the first instruction for the false-case scenario of the if-statement

## Query Example

for the function:

```solidity
function transfer(address _to, uint256 _amount) returns (bool success) 
     {
        if (_to == 0x0) throw;

        if (balances[msg.sender] >= _amount && _amount > 0 && balances[_to] + _amount > balances[_to]) 
        {
            balances[msg.sender] -= _amount;
            balances[_to] += _amount;
            Transfer(msg.sender, _to, _amount);
            return true;
         } 
         else 
         {
            return false;
         }
     }
```

The query (exec numbers are tuned here to match that exact if-statement)

```python
from glider import *

def query():
  instructionlist = Instructions().if_instructions().exec(1,1)
  
  first_false = instructionlist[0].first_false_instruction()

  return [first_false]
```

## Output Example

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
