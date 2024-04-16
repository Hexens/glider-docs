# Instructions.with\_callee\_function\_name\_prefix()

`with_callee_function_name_prefix(prefix: str, sensitivity: bool = True) →` [`Instructions`](./)

Adds a filter to get instructions that call a function whose name has the given prefix.

## Return type

`→` [`Instructions`](./)

## Query Example

```python
from glider import *

def query():
  instructions = (
    Instructions().
    with_callee_function_name_prefix("upgrade").
    exec(1)
  )

  return instructions
```

## Output Example

```solidity
{
    "contract":string"0x02551ded3f5b25f60ea67f258d907ed051e042b2"
    "contract_name":string"BasePatchFixRouter"
    "sol_function":solidity
        function atomicPatchAndUpgrade() external {
                require(msg.sender == OWNER);
                // First claim ownership via the transfer
                NOTIONAL.claimOwnership();
                NOTIONAL.upgradeToAndCall(
                    SELF,
                    abi.encodeWithSelector(BasePatchFixRouter.patchFix.selector)
                );
                NOTIONAL.upgradeTo(FINAL_ROUTER);
                // Do a direct transfer back to the owner
                NOTIONAL.transferOwnership(OWNER, true);
                // Safety check that we do not lose ownership
                require(NOTIONAL.owner() == OWNER);
                selfdestruct(payable(OWNER));
            }
    "sol_instruction":solidity
        NOTIONAL.upgradeToAndCall(
                    SELF,
                    abi.encodeWithSelector(BasePatchFixRouter.patchFix.selector)
                )
}
```
