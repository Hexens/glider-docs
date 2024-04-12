---
description: Adds a filter to get contracts that have an error with the given name.
---

# Contracts.with\_error\_name()

## Function Signature

`with_error_name(name: str, sensitivity: boot = True) ->` [`Contracts`](./)

## Query Example

```python
from glider import *

def query():
  contracts = Contracts().with_error_name("Invalid").exec(1)

  return contracts
```

## Output Example

<pre class="language-json"><code class="lang-json">{
    {
        "contract": "0x37d2127ed8fc713cbb30c8dd2f6ef6d329e43420",
<strong>        "contract_name": "MiyaMints"
</strong>    }
}
</code></pre>
