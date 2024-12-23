---
description: >-
  Adds a filter to get functions that have declarer contract with the given
  name.
---

# Functions.with\_declarer\_contract\_name()

The function adds a filter for the functions to be declared in a contract with a specific name.

## Example

```python
from glider import *

def query():
	# lets say we want to take transferFrom functions, but only from ERC721 contracts and not ERC20
    functions = Functions()\
        .with_name('transferFrom')\
        .with_declarer_contract_name('ERC721')\
        .exec(3)

    return functions
```

## Example Output

<figure><img src="../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>



{% hint style="info" %}
As can be seen, the output consists of the same function deployed under the same address but with different contract names, two of which are not ERC721. In fact, the query worked correctly, and the last two functions are included in the result as the function that is declared in ERC721 is, in fact, being inherited by those contracts.
{% endhint %}
