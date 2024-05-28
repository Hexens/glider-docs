---
description: >-
  Returns a Functions object representing the functions through which the
  function could be called
---

# Callable.extended\_callee\_functions()

`extended_callee_functions() ->` [`Functions`](../callables/functions/)

The function is the _extended_/_inter-procedural_ variant of [callee\_functions()](callable.callee\_functions.md), meaning it works recursively. It returns the Functions object representing all the functions through which the function could be called.&#x20;

The difference between `extended_callee_functions()` and `callee_functions()` the later one will only return direct callee functions, while the **extended** version will find all the functions recursively that eventually call the target function.

## Example

```python
from glider import *

def query():
    # find some internal function, at it will most probably have more callees
    functions = Functions().with_one_property([MethodProp.INTERNAL]).exec(1,1100)

    #lets take the first function from the result and return its extended_callee_functions
    output = functions[0].extended_callee_functions().exec()
    #print the code of the function, to be aware of whose callees we get
    print(functions[0].source_code())

    return output
```

For the function:

```solidity
function _execute(
        uint256 /* proposalId */,
        address[] memory targets,
        uint256[] memory values,
        bytes[] memory calldatas,
        bytes32 /*descriptionHash*/
    ) internal virtual {
        string memory errorMessage = "Governor: call reverted without message";
        for (uint256 i = 0; i < targets.length; ++i) {
            (bool success, bytes memory returndata) = targets[i].call{value: values[i]}(calldatas[i]);
            AddressUpgradeable.verifyCallResult(success, returndata, errorMessage);
        }
    }
```

the output will be:

## Example Output

```solidity
"root":{3 items
"contract":string"0xd747b21fb9120e2f02eb2f070b1f417d22387ea7"
"contract_name":string"AddressUpgradeable"
"sol_function":solidity
function verifyCallResult(
        bool success,
        bytes memory returndata,
        string memory errorMessage
    ) internal pure returns (bytes memory) {
        if (success) {
            return returndata;
        } else {
            _revert(returndata, errorMessage);
        }
    }
}
"root":{3 items
"contract":string"0xd747b21fb9120e2f02eb2f070b1f417d22387ea7"
"contract_name":string"AddressUpgradeable"
"sol_function":solidity
function _revert(bytes memory returndata, string memory errorMessage) private pure {
        // Look for revert reason and bubble it up if present
        if (returndata.length > 0) {
            // The easiest way to bubble the revert reason is using memory via assembly
            /// @solidity memory-safe-assembly
            assembly {
                let returndata_size := mload(returndata)
                revert(add(32, returndata), returndata_size)
            }
        } else {
            revert(errorMessage);
        }
    }
}
```
