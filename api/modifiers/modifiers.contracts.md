# Modifiers.contracts()

Returns Contracts object for the contracts of the modifiers.

## Return type

→ [Contracts](../contracts/)

An example to retrieve the contracts that the modifiers called `onlyOwner` are used within is as below

```python
from glider import *
def query():
  contractlist = Modifiers()\
      .with_name("onlyOwner")\
      .contracts()\
      .exec(5)
  return contractlist
```

## Output

```json
"root":{2 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"Ownable"
}
"root":{2 items
"contract":string"0x6f48d31eB35c9f52ef336aBf12f46E78F18fD7Fb"
"contract_name":string"VRF_Pizza_RNG"
}
"root":{2 items
"contract":string"0x31a13db822593aafef324ef2655e31b05b2577c0"
"contract_name":string"Ownable"
}
"root":{2 items
"contract":string"0x31a13db822593aafef324ef2655e31b05b2577c0"
"contract_name":string"TestCoin"
}
"root":{2 items
"contract":string"0xe5fA13058EdE558a2bFA675043f175148858A5F6"
"contract_name":string"Ownable"
}
```
