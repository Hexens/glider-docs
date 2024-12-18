---
description: Executes the formed query and returns a list of the Function objects.
---

# Functions.exec()

`exec(`_`limit_count: int = 0`_`,`` `_`offset_count: int = 0`_`) →` [`APIList`](../../iterables/apilist.md)`[`[`Function`](../../callable/function/)`]`

## Query Example

<pre class="language-python"><code class="lang-python"><strong>from glider import *
</strong>
def query():
  # Fetch a list of functions
  functions = Functions().exec(2)

  return functions
</code></pre>

## Output Example

<figure><img src="../../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>
