---
description: Classes that describe Solidity global variables
---

# GlobalVariables

These classes describe global variables, such as `msg.sender` and `block.timestamp`, in the glider.

* `MsgData` | Base: `GlobalVariabe` | object that represents `msg.data`
* `MsgGas` | Base: `GlobalVariable` | object that represents `msg.gas`
* `MsgSender` | Base: `GlobalVariable` | object that represents `msg.sender`&#x20;
* `MsgSig` | Base: `GlobalVariable` | object that represents `msg.sig`
* `MsgValue` | Base: `GlobalVariable` | object that represents `msg.value`
* `Now` | Base: `GlobalVariable` | object that represents `now`
* `TxGasprice` | Base: `GlobalVariable` | object that represents `tx.gasprice`
* `TxOrigin` | Base: `GlobalVariable` | object that represents `tx.origin`
* `GlobalVariable` | Base: Object&#x20;
