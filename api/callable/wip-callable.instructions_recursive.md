---
description: >-
  Returns the set of all instructions from the current function entry in the
  control flow graph.
---

# WIP Callable.instructions\_recursive()

`instructions_recursive() ->` [`APISet`](../iterables/apiset.md)`[`[`Instruction`](../instruction/)`]`

The function is the _**recursive**_**/**_**inter-procedural**_ variant of the [`instructions()`](callable.instructions.md), meaning that it works recursively. It returns a set of Instructions object representing all the instructions which are reachable from the target function, the differences between `instructions_recursive()` and `instructions()` the latter will only return instructions directly accessible from the function. At the same time, the recursive version will find all the instructions recursively, which are eventually called when executing the function.

Also, note that the return types of `instructions_recursive() -> APISet[Instruction]` and `instructions() -> Instructions` are different, the recursive version returns an APISet of Instruction objects, while the original one returns Instructions (queryable) object.

## Query Example

<pre class="language-python"><code class="lang-python"><strong>from glider import *
</strong>
def query():
    # lets find a function with name transferFrom
    functions = Functions().with_name('transferOwnership').exec(1)

    #print the code of the function
    print(functions[0].source_code())

    #return the list of (extended) instructions, as it return a set, we need to cast it to list
    return list(functions[0].extended_instructions())

</code></pre>

For the function:

```solidity
function transferOwnership(address newOwner) public virtual onlyOwner {
        require(newOwner != address(0), "Ownable: new owner is the zero address");
        _transferOwnership(newOwner);
    }
```

The output is:

## Example Output

<figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (127).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (128).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (130).png" alt=""><figcaption></figcaption></figure>
