---
description: >-
  Returns the set of all instructions from the current function entry in the
  control flow graph.
---

# Callable.extended\_instructions()

`extended_instructions() ->` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](../instruction/)`]`

The function is the _**extended**_**/**_**inter-procedural**_ variant of the [`instructions()`](callable.instructions.md), meaning that it works recursively. It returns a set of Instructions object representing all the instructions which are reachable from the target function, the differences between `extended_instructions()` and `instructions()` the latter will only return instructions directly accessible from the function. At the same time, the extended version will find all the instructions recursively, which are eventually called when executing the function.

Also, note that the return types of `extended_instructions() -> APISet[Instruction]` and `instructions() -> Instructions` are different, the extended version returns an APISet of Instruction objects, while the original one returns Instructions (queryable) object.

## Example

<pre class="language-python"><code class="lang-python"><strong>from glider import *
</strong>
def query():
    # lets find a function with name transferFrom
    functions = Functions().with_name('functionCallWithValue').exec(1)

    #print the code of the function
    print(functions[0].source_code())

    #return the list of (extended) instructions, as it return a set, we need to cast it to list
    return list(functions[0].extended_instructions())

</code></pre>

For the function:

```solidity
function functionCallWithValue(
        address target,
        bytes memory data,
        uint256 value
    ) internal returns (bytes memory) {
        return functionCallWithValue(target, data, value, "Address: low-level call with value failed");
    }
```

The output is:

## Example Output

```solidity
"root":{4 items
"contract":string"0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e"
"contract_name":string"Address"
"sol_function":solidity
function functionCallWithValue(
        address target,
        bytes memory data,
        uint256 value
    ) internal returns (bytes memory) {
        return functionCallWithValue(target, data, value, "Address: low-level call with value failed");
    }
"sol_instruction":solidity
return functionCallWithValue(target, data, value, "Address: low-level call with value failed")
},
...
"root":{4 items
"contract":string"0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e"
"contract_name":string"Address"
"sol_function":solidity
function functionCallWithValue(
        address target,
        bytes memory data,
        uint256 value,
        string memory errorMessage
    ) internal returns (bytes memory) {
        require(address(this).balance >= value, "Address: insufficient balance for call");
        require(isContract(target), "Address: call to non-contract");
 
        (bool success, bytes memory returndata) = target.call{value: value}(data);
        return verifyCallResult(success, returndata, errorMessage);
    }
"sol_instruction":solidity
bytes memory returndata
}
root":{4 items
"contract":string"0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e"
"contract_name":string"Address"
"sol_function":solidity
function functionCallWithValue(
        address target,
        bytes memory data,
        uint256 value,
        string memory errorMessage
    ) internal returns (bytes memory) {
        require(address(this).balance >= value, "Address: insufficient balance for call");
        require(isContract(target), "Address: call to non-contract");
 
        (bool success, bytes memory returndata) = target.call{value: value}(data);
        return verifyCallResult(success, returndata, errorMessage);
    }
"sol_instruction":solidity
require(address(this).balance >= value, "Address: insufficient balance for call")
},
...
"root":{4 items
"contract":string"0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e"
"contract_name":string"Address"
"sol_function":solidity
function verifyCallResult(
        bool success,
        bytes memory returndata,
        string memory errorMessage
    ) internal pure returns (bytes memory) {
        if (success) {
            return returndata;
        } else {
            // Look for revert reason and bubble it up if present
            if (returndata.length > 0) {
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
"sol_instruction":solidity
returndata.length > 0
}
...
```
