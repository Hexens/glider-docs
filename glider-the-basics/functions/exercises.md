# Exercises

## Intro

In this section, we will present several exercises that will fortify your Functions query skills. Each exercise provided comes along with a solution if you get stuck.



## **Exercise #1 - Finding Functions Named "buy"**

In our first exercise, we will look for functions named **buy**. Much like instructions, we have many Glider functions available to us that we can use to find functions. In this case, we are querying for function names.&#x20;

If we review the [Callables class Glider API documentation](https://glide.gitbook.io/main/api/callables), we can find several functions available to us to query functions by their name. &#x20;

**Challenge**: Update the query below to find functions named **buy**.

```python
from glider import *

def query():
    return (
        Functions()
        # CHALLENGE: Update the query to find functions named "buy." 
        .exec(10)
    )
```

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/LL7UG1Jy](https://glide.r.xyz/query/LL7UG1Jy)

</details>



## **Exercise #2 - Filtering Out Owner Functions**

Now that we have a query to find functions named **buy**, the next step is to filter out functions that can only be called by the contract owner.

While there are various ways a contract might restrict a function to owner-only access, we’ll focus on removing functions that use the **onlyOwner** modifier, as this is the most common approach developers use to enforce the owner-only restriction.

For example, we want to exclude this Solidity function from our results:

```solidity
// The onlyOwner modifier restricts this function to be called only 
// by the contract owner.
function buy(uint amount) external payable onlyOwner { 
    // Code omitted
}
```

If we review the Glider API documentation, we can find a [helpful function](https://glide.gitbook.io/main/api/functions/functions.without_modifier_name) to filter out functions that contain a specific modifier.

**Challenge**: Update the query to filter out functions that use the **onlyOwner** modifier.

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/HGzJCM2M](https://glide.r.xyz/query/HGzJCM2M)

</details>



## **Exercise #3 - Library Call Functions**

With our updated query, we can now identify functions named **buy** that can be called by anyone. Our next step is to identify **buy** functions that call a library function.

### **What Is a Solidity Library?**

A Solidity library is a piece of reusable code that contains one or more functions. Libraries can be injected into multiple Solidity contracts, making them a common way to reuse code across contracts.

### **Identifying Library Calls**

So far, we’ve focused on querying Solidity functions. However, if we review the [Glider API documentation](https://glide.gitbook.io/main/api/function), we’ll notice there’s no direct way to check if a Solidity function is calling a library function.

To query this, we can find library calls by first querying a function's instructions and then call Glider's [library\_calls()](https://glide.gitbook.io/main/api/instructions/instructions.library_calls) against the instructions.

### **Getting Instructions from Functions**

There’s one obstacle: How do we go from querying functions to querying a function's instructions?

Thankfully, Glider provides a solution. We can call `instructions()` on a list of Glider Functions, and it will return a list of Instructions, containing every instruction from each function.

Here’s what the Glider code would look like:

```python
functions = Functions().with_name("buy").exec(100)
instructions = functions.instructions()
```

With this approach, you can now query library calls by converting your list of functions into their corresponding instructions and identify library calls.

Once we have a list of instructions, we call the library\_calls() function from the Glider API. This will filter the results to include only instructions that contain library calls.

**Challenge**: Update the query from Exercise #2 to return instructions that are library calls in the **buy** function.

{% hint style="info" %}
Remember that exec() returns an [APIList](https://glide.gitbook.io/main/api/iterables/apilist). This means you can chain a method call to the list, and that method will be applied to every item in the list automatically.
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/SSXljjBX](https://glide.r.xyz/query/SSXljjBX)

</details>



## **Exercise #4 - Functions with More than 5 Parameters**

In this final exercise, we’ll update the query to only include **buy** functions that have more than 5 arguments.

To achieve this, we can use the `arguments()` method from the Glider API, which returns the arguments of a Solidity function. We can then use Python’s `len()` function to count the number of arguments returned.

{% hint style="info" %}
We can query for function arguments via the [arguments()](https://glide.gitbook.io/main/api/callable/callable.arguments) Glider method. This Glider function will return the functions arguments. Note that we need to also call list() on the arguments() return value. For example:

```python
function.arguments().list()
```
{% endhint %}

{% hint style="info" %}
We can then use Python's `len()` function to count the number of function arguments.
{% endhint %}

**Challenge**: Add a filter to your query that removes **buy** functions with fewer than 5 arguments.

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/BMNseYi2d](https://glide.r.xyz/query/BMNseYi2d)

</details>



## Bonus Challenge

Below we have a Glider query that finds the first function named **transferAll**.&#x20;

```python
from glider import *

def query():
    functions = (
        Functions()
        .with_name("transferAll")
        .exec(3) 
    )

    first_func = functions[0]

    # CHALLENGE: View the arguments of the first_func 
 
    return functions
```

**Challenge**: Identify the Glider function that will return a list of Solidity function arguments given a function.

{% hint style="info" %}
Glider functions inherit from the Callable class. Refer to the [Callable documentation](https://glide.gitbook.io/main/api/callable) to find the answer!
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/G9EgzuVP](https://glide.r.xyz/query/G9EgzuVP)

</details>

