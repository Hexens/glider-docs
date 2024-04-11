# Variables.with\_name()

## Return type

→ [Variables](./)

An example to retrieve variables with the name `owner` is as below

```python
from glider import *
def query():
  variablelist = Variables()\
      .with_name("owner")\
      .exec(5)
  return variablelist
```

## Output

```json
```
