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

```json
[
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": "function _msgSender() internal view virtual returns (address) {\n        return msg.sender;\n    }"
  },
  {
    "contract": "0x798AcB51D8FBc97328835eE2027047a8B54533AD",
    "contract_name": "Context",
    "sol_function": "function _msgData() internal view virtual returns (bytes calldata) {\n        return msg.data;\n    }"
  }
]
```
