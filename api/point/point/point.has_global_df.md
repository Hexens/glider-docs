---
description: >-
  Returns true if the point has a dependency on external variables in the
  current data flow graph, false otherwise.
---

# Point.has\_global\_df()

`has_global_df() → bool`

## Query Example

```python
def query():
  instructions = (
    Instructions()
    .exec(10, 10)
    .filter(lambda x: x.has_global_df())
  )
  
  print(len(instructions))
  
  return instructions
```

## Output Example

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



