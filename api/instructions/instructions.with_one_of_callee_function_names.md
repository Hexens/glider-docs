# Instructions.with\_one\_of\_callee\_function\_names()

`with_one_of_callee_function_names(names: List[str], sensitivity: bool = True) →` [`Instructions`](./)

Adds a filter to get [Instructions](./) that call a function with the given signature.

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = (
    Instructions().
    with_one_of_callee_function_names(["deposit", "withdraw"]).
    exec(2)
  )

  return instructions
```

## Output Example

<pre class="language-solidity"><code class="lang-solidity">{
    {
        "contract": "0x23297ee054e8f600af482013ddbe856b7178a7d3"
<strong>        "contract_name": "WETH9"
</strong>        "sol_function": 
            function() external payable {
                    deposit();
                }
        "sol_instruction": 
            deposit()
    },
    {
        "contract": "0x23297ee054e8f600af482013ddbe856b7178a7d3"
        "contract_name": "ZeroExV3ExchangeWrapper"
        "sol_function":
            function exchange(
                    address tradeOriginator,
                    address receiver,
                    address makerToken,
                    address takerToken,
                    uint256 requestedFillAmount,
                    bytes calldata orderData
                )
                    external
                    returns (uint256)
                {
                    // prepare the exchange
                    (LibOrder.Order memory order, bytes memory signature) = parseSignedOrder(
                        orderData,
                        makerToken,
                        takerToken
                    );
            
                    // make sure that the exchange can take the tokens from this contract
                    takerToken.ensureAllowance(
                        ZERO_EX_TOKEN_PROXY,
                        requestedFillAmount
                    );
            
                    // execute fill order
                    IExchange v3Exchange = IExchange(ZERO_EX_EXCHANGE);
                    LibFillResults.FillResults memory fill = v3Exchange.fillOrKillOrder(
                        order,
                        requestedFillAmount,
                        signature
                    );
            
                    // set allowance
                    makerToken.ensureAllowance(receiver, fill.makerAssetFilledAmount);
            
                    // return excess ETH to the trade originator in the event of protocol fee overpayment
                    uint256 protocolFeeRefund = WETH.balanceOf(address(this));
                    if (makerToken == address(WETH)) {
                        protocolFeeRefund = protocolFeeRefund.sub(fill.makerAssetFilledAmount);
                    }
                    if (protocolFeeRefund != 0) {
                        WETH.withdraw(protocolFeeRefund);
                        address(uint160(tradeOriginator)).transfer(protocolFeeRefund);
                    }
            
                    return fill.makerAssetFilledAmount;
                }
        "sol_instruction":
            WETH.withdraw(protocolFeeRefund)
    }

}
</code></pre>
