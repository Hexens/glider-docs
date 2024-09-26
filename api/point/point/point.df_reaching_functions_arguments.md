---
description: >-
  Returns the list of pairs, where the first element is the function and the
  second element is the argument to which data flow reaches from the point (it
  may reach through a chain of calls).
---

# Point.df\_reaching\_functions\_arguments()

`df_reaching_functions_arguments() →` [`APIList`](../../iterables/apilist.md)`[Tuple[`[`Callable`](../../callable/)`, int]]`

## Query Example

```python
from glider import *

def query():

  instructions = Instructions().exec(1, 77)
  for ins in instructions:
    reaching_points = ins.df_reaching_functions_arguments()
    for reaching_point in reaching_points:
      print(f"Point: {reaching_point[0].source_code()} | Argument index {reaching_point[1]}")
  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/Screenshot 2024-09-26 at 19.56.11.png" alt=""><figcaption></figcaption></figure>

### Here is a more detailed output

```solidity
Point1: 
function isContract(address account) internal view returns (bool) {
        // This method relies on extcodesize/address.code.length, which returns 0
        // for contracts in construction, since the code is only stored at the end
        // of the constructor execution.

        return account.code.length &gt; 0;
} 
ArgumentIndex1: 0
=====================================================================================
Point2: function verifyCallResult(
        bool success,
        bytes memory returndata,
        string memory errorMessage
    ) internal pure returns (bytes memory) {
        if (success) {
            return returndata;
        } else {
            // Look for revert reason and bubble it up if present
            if (returndata.length &gt; 0) {
                // The easiest way to bubble the revert reason is using memory via assembly

                assembly {
                    let returndata_size := mload(returndata)
                    revert(add(32, returndata), returndata_size)
                }
            } else {
                revert(errorMessage);
            }
        }
    }
ArgumentIndex2: 1
=====================================================================================
Point3: 
function verifyCallResult(
        bool success,
        bytes memory returndata,
        string memory errorMessage
    ) internal pure returns (bytes memory) {
        if (success) {
            return returndata;
        } else {
            // Look for revert reason and bubble it up if present
            if (returndata.length &gt; 0) {
                // The easiest way to bubble the revert reason is using memory via assembly

                assembly {
                    let returndata_size := mload(returndata)
                    revert(add(32, returndata), returndata_size)
                }
            } else {
                revert(errorMessage);
            }
        }
}
ArgumentIndex3: 0
=====================================================================================
Point4: 
function functionDelegateCall(address target, bytes memory data) internal returns (bytes memory) {
        return functionDelegateCall(target, data, "Address: low-level delegate call failed");
}
ArgumentIndex4: 0
=====================================================================================
Point5: 
function functionDelegateCall(
        address target,
        bytes memory data,
        string memory errorMessage
    ) internal returns (bytes memory) {
        require(isContract(target), "Address: delegate call to non-contract");

        (bool success, bytes memory returndata) = target.delegatecall(data);
        return verifyCallResult(success, returndata, errorMessage);
} 
ArgumentIndex5: 0
```
