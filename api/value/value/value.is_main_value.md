---
description: Returns true if the value doesn't have a parent value, false otherwise
---

# Value.is\_main\_value()

`is_main_value() → bool`

**Query Example**

```python
from glider import *

def query():
    instructions = Instructions().exec(1, 5)
    for instruction in instructions:
        components = instruction.get_components()
        for component in components:
            print(component.is_main_value())
            if component.is_main_value():
                print(component.expression)
    return instructions
```

**Output**

<figure><img src="../../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>
