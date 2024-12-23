# Functions.with\_declarer\_contract\_name()

`with_declarer_contract_name(`_`name: str`_`,`` `_`sensitivity: bool = True`_`) →` [`Functions`](./)

Adds a filter to get functions that have direct declarer contract with the given name.

## Example

```python
from glider import *

def query():
  
  # Fetch a list of functions with declarer contract name 'Vault'
  functions = Functions().with_declarer_contract_name('Vault').exec(5)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
