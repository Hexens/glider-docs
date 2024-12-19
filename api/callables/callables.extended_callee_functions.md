---
description: >-
  Returns a Functions object representing the functions which are called from
  the callables of the Callables object.
---

# Callables.extended\_callee\_functions()

`extended_callee_functions() →` [`Functions`](functions/)

## Query Example

```python
from glider import *

def query():
  functions = Functions().with_name("beforeTokenTransfer").exec(1)
  print(functions)
  callee_functions = []
  for func in functions:
    for callee_func in func.extended_callee_functions().exec():
      callee_functions.append(callee_func)

  return callee_functions
```

## Output Example

<figure><img src="../../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (144).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (145).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (147).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (149).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (151).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (152).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (153).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (158).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (159).png" alt=""><figcaption></figcaption></figure>
