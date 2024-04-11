# Callables.contracts()

Returns the [Contracts](../contracts/) object for the contracts of the callables. This method can be called on all [Callables](./) child classes: [Functions](../functions/) and [Modifiers](../modifiers/).

### Functions Example

```python
from glider import *

def query():
  # Retrieve the contracts of a list of functions
  contracts = Functions().contracts().exec(100)

  # Return the first five contracts
  return contracts[:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Context"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "IERC165"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "ERC165"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "IERC721"
    }
]
```

### Modifiers Example

```python
from glider import *

def query():
  # Retrieve the contracts of a list of modifiers
  contracts = Modifiers().contracts().exec(100)

  # Return the first five contracts
  return contracts[0:5]
```

Output:

```json
[
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "Ownable"
    },
    {
        "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
        "contract_name": "LTP"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "Owned"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "RewardsDistributionRecipient"
    },
    {
        "contract": "0x0c16f70dBBbCB63a81de06eB2fc2ABE4a19f89F2",
        "contract_name": "ReentrancyGuard"
    }
]
```
