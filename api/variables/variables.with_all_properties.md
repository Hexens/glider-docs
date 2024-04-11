# Variables.with\_all\_properties()

Adds a filter to get [variables](./) that have all given [properties](../variable/variable.properties.md).

## Return type

→ [Variables](./)

An example to retrieve all variables with the properties of [VariableProp.CONSTANT](../variableprop/variableprop.constant.md) and [VariableProp.PUBLIC](../variableprop/variableprop.public.md) is as below

```python
from glider import *
def query():
  variablelist = Variables()\
      .with_all_properties([VariableProp.CONSTANT,VariableProp.PUBLIC])\
      .exec(5)
  return variablelist
```

## Output

```json
```
