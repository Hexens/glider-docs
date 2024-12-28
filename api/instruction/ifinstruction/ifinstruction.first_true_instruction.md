# IfInstruction.first\_true\_instruction()

`first_true_instruction() →` [`Instruction`](../)

The function returns the first instruction for the true-case scenario of the if-statement

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
  
  first_true = instructionlist[0].first_true_instruction()

  return [first_true]
```

## Output

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The [next\_instruction()](../instruction.next_instruction.md) is not used as it will always return an empty list of instructions. This is because no instruction can be run after a return statement, and the [next\_instruction()](../instruction.next_instruction.md) is non-recursive (intra-procedural).
{% endhint %}
