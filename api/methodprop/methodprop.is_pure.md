# MethodProp.IS\_PURE

In a smart contract a function can be declared that neither reads nor modifies any state variables. These functions can be marked as PURE functions

An example of such a function is:

```solidity
function add(uint256 a,uint256 b) external pure returns uint256 {
	return a + b;
}
```

An example of a query that would select functions marked as pure functions is:

```python
from glider import *
def query():
  props_included = [MethodProp.IS_PURE]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

```json
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"IConstantFlowAgreementV1"
"sol_function":solidity
function agreementType() external override pure returns (bytes32) {
        return keccak256("org.superfluid-finance.agreements.ConstantFlowAgreement.v1");
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Address"
"sol_function":solidity
function verifyCallResult(
        bool success,bytes memory returndata,string memory errorMessage
    ) internal pure returns (bytes memory) {
        if (success) {
            return returndata;
        } else {
            
            if (returndata.length > 0) {
                
 
                assembly {
                    let returndata_size := mload(returndata)
                    revert(add(32,returndata),returndata_size)
                }
            } else {
                revert(errorMessage);
            }
        }
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Strings"
"sol_function":solidity
function toString(uint256 value) internal pure returns (string memory) {
        
        
 
        if (value == 0) {
            return "0";
        }
        uint256 temp = value;
        uint256 digits;
        while (temp != 0) {
            digits++;
            temp /= 10;
        }
        bytes memory buffer = new bytes(digits);
        while (value != 0) {
            digits -= 1;
            buffer[digits] = bytes1(uint8(48 + uint256(value % 10)));
            value /= 10;
        }
        return string(buffer);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Strings"
"sol_function":solidity
function toHexString(uint256 value) internal pure returns (string memory) {
        if (value == 0) {
            return "0x00";
        }
        uint256 temp = value;
        uint256 length = 0;
        while (temp != 0) {
            length++;
            temp >>= 8;
        }
        return toHexString(value,length);
    }
}
"root":{3 items
"contract":string"0x798AcB51D8FBc97328835eE2027047a8B54533AD"
"contract_name":string"Strings"
"sol_function":solidity
function toHexString(uint256 value,uint256 length) internal pure returns (string memory) {
        bytes memory buffer = new bytes(2 * length + 2);
        buffer[0] = "0";
        buffer[1] = "x";
        for (uint256 i = 2 * length + 1; i > 1; --i) {
            buffer[i] = _HEX_SYMBOLS[value & 0xf];
            value >>= 4;
        }
        require(value == 0,"Strings: hex length insufficient");
        return string(buffer);
    }
}
```
