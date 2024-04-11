# Variables.exec()

Executes the formed query and returns a list of [Variable](../variable/) objects.

## Return type

→ List\[[Variable](../variable/)]

It accepts two integer parameters the first one is `limit_count` which limits the count of the returned results and the second is `offset_count` which sets the offset from which the result set must be returned.

An example to retrieve varaibles is as below

```python
from glider import *
def query():
  variablelist = Variables()\
      .exec(5)
  return variablelist
```

## Output

```json
```
