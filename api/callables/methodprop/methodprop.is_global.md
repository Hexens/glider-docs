# MethodProp.IS\_GLOBAL

A global function is defined outside of any contract scope.

An example of a global function is:

```solidity
pragma solidity ^0.7.0;

// solhint-disable

/**
 * @dev Reverts if `condition` is false, with a revert reason containing `errorCode`. Only codes up to 999 are
 * supported.
 */
function _require(bool condition, uint256 errorCode) pure {
    if (!condition) _revert(errorCode);
}
```

An example query to filter these functions:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_GLOBAL]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(1)
  print(functions[0].source_code())
  print(functions[0].address())
  return []
```

Output:

```solidity
"root":{1 item
"print_output":[2 items
0:string"function _require(bool condition, uint256 errorCode) pure {
    if (!condition) _revert(errorCode);
}"
1:string"0x0d968094e386f9fbfb3797655ab8e4672c2cb737"
]
}
```

