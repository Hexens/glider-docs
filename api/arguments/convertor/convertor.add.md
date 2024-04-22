---
description: Add a new conversion.
---

# Convertor.add()

**`add`**`(`_`from_type: str`_`,`` `_`to_type: str`_`) → None`



```python
from glider import *

def query():
  # Create a Convertor object 
  convertor = Convertor()

  # Add a conversion from address to bytes20
  convertor.add("uint160", "address")

  # Fetch a list of functions
  funs = Functions().with_arg_type('uint160').exec(1,100)
  # Return the functions with at least one argument convertible to bytes20
  # It will be only the argument of type address
  output = []
  for fun in funs:
    args = fun.arguments().with_type_convertible(["address"], convertor)
    if args:
      output.append(fun)
  return output
```

Output (first result only):

```solidity
"root":{3 items
"contract":string"0x4109ab7966c5461439bdb0beda92c92fec767966"
"contract_name":string"UniswapV3Pool"
"sol_function":solidity
function initialize(uint160 sqrtPriceX96) external override {
        require(slot0.sqrtPriceX96 == 0, 'AI');
 
        int24 tick = TickMath.getTickAtSqrtRatio(sqrtPriceX96);
 
        (uint16 cardinality, uint16 cardinalityNext) = observations.initialize(_blockTimestamp());
 
        slot0 = Slot0({
            sqrtPriceX96: sqrtPriceX96,
            tick: tick,
            observationIndex: 0,
            observationCardinality: cardinality,
            observationCardinalityNext: cardinalityNext,
            feeProtocol: 0,
            unlocked: true
        });
 
        emit Initialize(sqrtPriceX96, tick);
    }
}
  "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
  "contract_name": "Ownable",
  "sol_function": "function transferOwnership(address newOwner) public virtual onlyOwner {\n        require(newOwner != address(0),\"Ownable: new owner is the zero address\");\n        _setOwner(newOwner);\n    }"
}

```

Note that the order of the arguments is important. In the above example, only conversions from `address` to `bytes20` are allowed and not from `bytes20` to `address`.
