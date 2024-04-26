# Function.return\_tuple()

`return_tuple() → List[Tuple[Type, str]]`

Returns the function's `return (type, value)` tuples.

## Example

```python
from glider import *

def query():
  # Fetch a list of functions
  functions = Functions().exec(1)

  # Retrieve the return instructions of the first function
  tuple_list = functions[0].return_tuple()
  for tup in tuple_list:
    for var in tup:
      print(var.name)

  return functions
```



## Output

```solidity
"root":{3 items
"contract":string"0xd705c24267ed3c55458160104994c55c6492dfcf"
"contract_name":string"Context"
"sol_function":solidity
function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }
}

"root":{1 item
"print_output":[2 items
0:string"address"
1:string"None"
]

```
