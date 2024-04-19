---
description: Adds a filter to get contracts whose names have the given prefix.
---

# Contracts.name\_prefix()

`name_prefix(prefix: str, sensitivity: bool = True) ->` [`Contracts`](./)



## Query Example

```python
from glider import *

def query():

  main_contracts = Contracts().name_prefix("Access", sensitivity=True).exec(1)

  return main_contracts
```

## Output Example

<pre class="language-python"><code class="lang-python"><strong>{
</strong><strong>    {
</strong>        "contract": "0xfb10b1b0f68b3eaaca1ecd12a47cf7f55beabb98",
        "contract_name": "AccessControlRegistryAdminned"
    }
}
</code></pre>
