# Callables.with\_name\_regexes()

`with_name_regexes(`_`regexes: List[str]`_`) →` [`Callables`](./)\


Adds a filter to get callables whose names match any of the regex expressions from the given list. Returns a filtered [Callables](./) child object. This method can be called on all [Callables](./) child classes: [Functions](functions/) and [Modifiers](modifiers/).

To filter given a single regex expression, refer to [Callables.with\_name\_regex()](callables.with_name_regex.md).

### Functions Example

```python
from glider import *

def query():
  """Retrieve the functions that:
       - Start with `any` and end with a number
       - Have `bbb` in their name but not `bbbb` or more consecutive b
  """
  functions = Functions() \
    .with_name_regexes([
      r"^any.*\d$",
      r"(?<!b)b{3}(?!b)"
    ]) \
    .exec(100)

  # Return the first five functions
  return functions[:5]
```

Output:

<figure><img src="../../.gitbook/assets/image (164).png" alt=""><figcaption></figcaption></figure>

### Modifiers Example

<pre class="language-python"><code class="lang-python"><strong>from glider import *
</strong>
def query():
  """Retrieve the modifiers that:
      - Start with `p` and end with `d`
      - Start with `l` and end with `d`
  """
  modifiers = Modifiers() \
    .with_name_regexes([
      r"^p.*d$",
      r"^l.*d$"
    ]) \
    .exec(100)

  # Return the first five modifiers
  return modifiers[:5]
</code></pre>

Output:

<figure><img src="../../.gitbook/assets/image (165).png" alt=""><figcaption></figcaption></figure>
