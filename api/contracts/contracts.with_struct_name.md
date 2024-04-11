---
description: Adds a filter to get contracts that have a struct with the given name.
---

# Contracts.with\_struct\_name()

Input:

```python
from glider import *

def query():

  contracts = Contracts().with_struct_name("User").exec(100)

  # Return the first five functions
  return contracts[0:5]
```

Output:

```python
"root":{2 items
"contract":string"0x34fc971063aa11e570929427c26479d7b8dd7dd1"
"contract_name":string"MUSUBIV3"
}
"root":{2 items
"contract":string"0xb3c21C93f3cB62bb2d34cfF51698149ceD83A0b0"
"contract_name":string"Subscribe"
}
"root":{2 items
"contract":string"0x9EbE005953d579a1AcAE36ee8054AfD48e9A1FB2"
"contract_name":string"TaxVendorPol"
}
"root":{2 items
"contract":string"0xdB1B2cCdca2142a6297994101E83Da279F6c20dD"
"contract_name":string"PolkaBridgeLaunchPad"
}
"root":{2 items
"contract":string"0xc0159c36060C5d5bF60bf26330A01e88f9FdAfFc"
"contract_name":string"Mobwibsol"
}
```

