# MethodProp.HAS\_ERRORS

The HAS\_ERRORS property is used to add a filter to include or exclude functions that revert with an error.

In solidity a smart contract a developer can define custom errors which are then called when an error is raised.

An example of such a contract would be as below:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Example {
    error myCustomError(uint256 requestedAmount,address caller);

    function collectAllowance(address caller,uint256 requestedAmount) public returns (bool success){
            //just revert to show how errors work
            revert myCustomError(requestedAmount,caller);
    }

}
```

An example of a query which would filter to include functions that use errors is&#x20;

```python
from glider import *
def query():
  props_included = [MethodProp.HAS_ERRORS]
  functions = Functions()\
      .with_all_properties(props_included)\
      .exec(5)

  return functions
```

## Output

```json
"root":{3 items
"contract":string"0xe90baa4A5fD4fE25443d27e6E2883350a0E67855"
"contract_name":string"Bulker"
"sol_function":solidity
function invoke(uint[] calldata actions,bytes[] calldata data) external payable {
        if (actions.length != data.length) revert InvalidArgument();
 
        uint unusedEth = msg.value;
        for (uint i = 0; i < actions.length; ) {
            uint action = actions[i];
            if (action == ACTION_SUPPLY_ASSET) {
                (address to,address asset,uint amount) = abi.decode(data[i],(address,address,uint));
                supplyTo(to,asset,amount);
            } else if (action == ACTION_SUPPLY_ETH) {
                (address to,uint amount) = abi.decode(data[i],(address,uint));
                unusedEth -= amount;
                supplyEthTo(to,amount);
            } else if (action == ACTION_TRANSFER_ASSET) {
                (address to,address asset,uint amount) = abi.decode(data[i],(address,address,uint));
                transferTo(to,asset,amount);
            } else if (action == ACTION_WITHDRAW_ASSET) {
                (address to,address asset,uint amount) = abi.decode(data[i],(address,address,uint));
                withdrawTo(to,asset,amount);
            } else if (action == ACTION_WITHDRAW_ETH) {
                (address to,uint amount) = abi.decode(data[i],(address,uint));
                withdrawEthTo(to,amount);
            }
            unchecked { i++; }
        }
 
        
        if (unusedEth > 0) {
            (bool success,) = msg.sender.call{ value: unusedEth }("");
            if (!success) revert FailedToSendEther();
        }
    }
}
"root":{3 items
"contract":string"0xe90baa4A5fD4fE25443d27e6E2883350a0E67855"
"contract_name":string"Bulker"
"sol_function":solidity
function withdrawEthTo(address to,uint amount) internal {
        amount = getAmount(weth,amount);
        CometInterface(comet).withdrawFrom(msg.sender,address(this),weth,amount);
        IWETH9(weth).withdraw(amount);
        (bool success,) = to.call{ value: amount }("");
        if (!success) revert FailedToSendEther();
    }
}
"root":{3 items
"contract":string"0xe90baa4A5fD4fE25443d27e6E2883350a0E67855"
"contract_name":string"CometMath"
"sol_function":solidity
function safe64(uint n) internal pure returns (uint64) {
        if (n > type(uint64).max) revert InvalidUInt64();
        return uint64(n);
    }
}
"root":{3 items
"contract":string"0xe90baa4A5fD4fE25443d27e6E2883350a0E67855"
"contract_name":string"CometMath"
"sol_function":solidity
function safe104(uint n) internal pure returns (uint104) {
        if (n > type(uint104).max) revert InvalidUInt104();
        return uint104(n);
    }
}
"root":{3 items
"contract":string"0xe90baa4A5fD4fE25443d27e6E2883350a0E67855"
"contract_name":string"CometMath"
"sol_function":solidity
function safe128(uint n) internal pure returns (uint128) {
        if (n > type(uint128).max) revert InvalidUInt128();
        return uint128(n);
    }
}
```
