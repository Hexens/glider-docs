# Variables.with\_one\_property()

Adds a filter to get [variables](./) that at least have one of the given [properties](../variable/variable.properties.md).

## Return type

→ [Variables](./)

An example to retrieve all variables with the only property being [VariableProp.CONSTANT](../variableprop/variableprop.constant.md) is as below

```python
rom glider import *
def query():
  variablelist = Variables()\
      .with_one_properties([VariableProp.PUBLIC])\
      .exec(5)
  return variablelist
```

## Output

```json
```
