---
description: Returns Value representing the gas-parameter used in the external calls.
---

# Call.get\_call\_gas()

`get_call_gas() → List[`[`Value`](../value/)`]`



**Query Example**

```python
from glider import *

def query():
  instructions = Instructions().low_level_function_calls().exec(100)

  output = []

  for entry_ins in instructions:
    for next_ins in entry_ins.next_instructions():
      for call in next_ins.get_callee_values():
          output.append(next_ins)
          for arg in call.get_call_gas():
            print(arg, arg.expression)
            return [next_ins]

  return output
```

**Output**

```solidity
"root":{4 items
"contract":string"0xe941bd60bd0c92605f8d90992c7dce3c5fc229f3"
"contract_name":string"ERC20ByMetadrop"
"sol_function":solidity
function _swapTaxForNative(
    uint256 swapBalance_,
    uint256 contractBalance_
  ) internal {
    uint256 preSwapBalance = address(this).balance;
 
    address[] memory path = new address[](2);
    path[0] = address(this);
    path[1] = _uniswapRouter.WETH();
 
    // Wrap external calls in try / catch to handle errors
    try
      _uniswapRouter.swapExactTokensForETHSupportingFeeOnTransferTokens(
        swapBalance_,
        0,
        path,
        address(this),
        block.timestamp + 600
      )
    {
      uint256 postSwapBalance = address(this).balance;
 
      uint256 balanceToDistribute = postSwapBalance - preSwapBalance;
 
      uint256 totalPendingSwap = projectTaxPendingSwap + metadropTaxPendingSwap;
 
      uint256 projectBalanceToDistribute = (balanceToDistribute *
        projectTaxPendingSwap) / totalPendingSwap;
 
      uint256 metadropBalanceToDistribute = (balanceToDistribute *
        metadropTaxPendingSwap) / totalPendingSwap;
 
      // We will not have swapped all tax tokens IF the amount was greater than the max auto swap.
      // We therefore cannot just set the pending swap counters to 0. Instead, in this scenario,
      // we must reduce them in proportion to the swap amount vs the remaining balance + swap
      // amount.
      //
      // For example:
      //  * swap Balance is 250
      //  * contract balance is 385.
      //  * projectTaxPendingSwap is 300
      //  * metadropTaxPendingSwap is 85.
      //
      // The new total for the projectTaxPendingSwap is:
      //   = 300 - ((300 * 250) / 385)
      //   = 300 - 194
      //   = 106
      // The new total for the metadropTaxPendingSwap is:
      //   = 85 - ((85 * 250) / 385)
      //   = 85 - 55
      //   = 30
      //
      if (swapBalance_ < contractBalance_) {
        projectTaxPendingSwap -= uint128(
          (projectTaxPendingSwap * swapBalance_) / contractBalance_
        );
        metadropTaxPendingSwap -= uint128(
          (metadropTaxPendingSwap * swapBalance_) / contractBalance_
        );
      } else {
        (projectTaxPendingSwap, metadropTaxPendingSwap) = (0, 0);
      }
      // Distribute to treasuries:
      bool success;
      address weth;
      uint256 gas;
 
      if (projectBalanceToDistribute > 0) {
        // If no gas limit was provided or provided gas limit greater than gas left, just use the remaining gas.
        gas = (CALL_GAS_LIMIT == 0 || CALL_GAS_LIMIT > gasleft())
          ? gasleft()
          : CALL_GAS_LIMIT;
 
        // We limit the gas passed so that a called address cannot cause a block out of gas error:
        (success, ) = projectTaxRecipient.call{
          value: projectBalanceToDistribute,
          gas: gas
        }("");
 
        // If the ETH transfer fails, wrap the ETH and send it as WETH. We do this so that a called
        // address cannot cause this transfer to fail, either intentionally or by mistake:
        if (!success) {
          if (weth == address(0)) {
            weth = _uniswapRouter.WETH();
          }
 
          try IWETH(weth).deposit{value: projectBalanceToDistribute}() {
            try
              IERC20(address(weth)).transfer(
                projectTaxRecipient,
                projectBalanceToDistribute
              )
            {} catch {
              // Dont allow a failed external call (in this case to WETH) to stop a transfer.
              // Emit that this has occured and continue.
              emit ExternalCallError(1);
            }
          } catch {
            // Dont allow a failed external call (in this case to WETH) to stop a transfer.
            // Emit that this has occured and continue.
            emit ExternalCallError(2);
          }
        }
      }
 
      if (metadropBalanceToDistribute > 0) {
        // If no gas limit was provided or provided gas limit greater than gas left, just use the remaining gas.
        gas = (CALL_GAS_LIMIT == 0 || CALL_GAS_LIMIT > gasleft())
          ? gasleft()
          : CALL_GAS_LIMIT;
 
        (success, ) = metadropTaxRecipient.call{
          value: metadropBalanceToDistribute,
          gas: gas
        }("");
 
        // If the ETH transfer fails, wrap the ETH and send it as WETH. We do this so that a called
        // address cannot cause this transfer to fail, either intentionally or by mistake:
        if (!success) {
          if (weth == address(0)) {
            weth = _uniswapRouter.WETH();
          }
          try IWETH(weth).deposit{value: metadropBalanceToDistribute}() {
            try
              IERC20(address(weth)).transfer(
                metadropTaxRecipient,
                metadropBalanceToDistribute
              )
            {} catch {
              // Dont allow a failed external call (in this case to WETH) to stop a transfer.
              // Emit that this has occured and continue.
              emit ExternalCallError(3);
            }
          } catch {
            // Dont allow a failed external call (in this case to WETH) to stop a transfer.
            // Emit that this has occured and continue.
            emit ExternalCallError(4);
          }
        }
      }
    } catch {
      // Dont allow a failed external call (in this case to uniswap) to stop a transfer.
      // Emit that this has occured and continue.
      emit ExternalCallError(5);
    }
  }
"sol_instruction":solidity
(success, ) = metadropTaxRecipient.call{
          value: metadropBalanceToDistribute,
          gas: gas
        }("")
}
"root":{1 item
"print_output":[2 items
0:string"<api.value.Var object at 0x7fd83dc6bf50>"
1:string"gas"
]
}
```
