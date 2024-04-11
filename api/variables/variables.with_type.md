# Variables.with\_type()

Adds a filter to get [variables](./) that have the given [type](../variable/variable.type.md).

## Return type

→ [Variables](./)

Get a list of of variables based on the declared type

```python
from glider import *
def query():
  variablelist = Variables()\
      .with_type("address")\
      .exec(5)
  return variablelist
```

## Output

```json
```
