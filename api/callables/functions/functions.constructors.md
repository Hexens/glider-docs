# Functions.constructors()

`constructors() →` [`Functions`](./)

Adds a filter to get only the constructors.

## Example

```python
from glider import *

def query():
  # Fetch a list of constructors
  functions = Functions().constructors().exec(2)

  return functions
```

## Output

<figure><img src="../../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

## Old constructor syntax

The function also accounts for the old constructor syntax, which in the older Solidity versions was named the same as the contract.&#x20;

```python
from glider import *

def query():
  funcs = Functions().constructors().without_name('constructor').exec(2)
  return funcs
```

Output

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

