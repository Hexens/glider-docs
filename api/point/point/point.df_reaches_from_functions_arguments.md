---
description: >-
  Returns the list of pairs, where the first element is the function and the
  second element the argument number from which data flow reaches to the point
  (it may reach through a chain of calls).
---

# Point.df\_reaches\_from\_functions\_arguments()

`df_reaches_from_functions_arguments() →` [`APIList`](../../iterables/apilist.md)`[Tuple[`[`Callable`](../../callable/)`, int]]`



## Query Example

```python
from glider import *

def query():

  instructions = Instructions().exec(1, 77)
  for ins in instructions:
    reaching_points = ins.df_reaches_from_functions_arguments()
    for reaching_point in reaching_points:
      print(f"Point: {reaching_point[0].source_code()} | Argument index {reaching_point[1]}")
  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Here is a more detailed output

```solidity
Point: 
constructor(bytes memory _a, bytes memory _data) payable {
        (address _as) = abi.decode(_a, (address));
        assert(KEY == bytes32(uint256(keccak256("eip1967.proxy.implementation")) - 1));
        require(Address.isContract(_as), "address error");
        StorageSlot.getAddressSlot(KEY).value = _as;
        if (_data.length &gt; 0) {
            Address.functionDelegateCall(_as, _data);
        }
}
ArgumentIndex: 0
```
