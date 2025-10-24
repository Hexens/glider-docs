# Exercises

## Intro

In this section, we will present several exercises that will fortify your Instructions query skills. Each exercise provided comes along with a solution if you get stuck.



## **Exercise #1 - Find external calls**

Now, let’s update this query to find instructions that make external calls to other contracts. To achieve this, we can reference the [Instructions() section](https://glide.gitbook.io/main/glider-ide/api/instructions) of the Glider API documentation to identify the function that queries for external calls.

**Challenge**: Update the following query such that it queries for external call instructions:

```python
from glider import *

def query():
    # CHALLENGE: Update this query such that it looks for external call instructions.
    return Instructions().exec(10)
```

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/4aKXz8r5](https://glide.r.xyz/query/4aKXz8r5)

</details>



## **Exercise #2 - Find the Instructions that Follow External Calls**

Now that we’ve identified external call instructions, let’s take it a step further and find the instructions executed immediately after those external calls.

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-09 at 2.11.36 PM.png" alt=""><figcaption><p>Instructions following an external call instruction are highlighted in blue</p></figcaption></figure>

To achieve this, we need to iterate over each instruction and check how many next instructions exist. If 1 or more instructions do exist, then we have a positive hit.

{% hint style="info" %}
Refer to this [Glider method](https://glide.gitbook.io/main/glider-ide/api/instruction/instruction.next_instructions) to learn how to retrieve an instruction’s next instructions.
{% endhint %}

**Challenge**: Update the query below to only return external call instructions that are followed by other instructions.

**Extra Challenge:** Use the filter() function to exclude instructions that don’t have any next instructions.

```python
from glider import *

def query():
    return (
        Instructions()
        .external_calls()
        .exec(10)
        # CHALLENGE: Add your solution here.
    )
```

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/BXFNHQyC](https://glide.r.xyz/query/BXFNHQyC)

</details>



## **Exercise #3 - Return instructions that Write to Storage**

Now that we’ve identified cases where additional instructions are executed after an external call, let’s take it further by examining these instructions to see if any of them write to the contract’s storage (i.e., update a state variable).

To check if an instruction is writing to contract storage, Glider provides a [dedicated method named is\_storage\_write()](https://glide.gitbook.io/main/glider-ide/api/instruction/instruction.is_storage_write) we can use. This function allows us to determine whether a given instruction performs a write operation on the contract’s state.

**Challenge**: Use the `is_storage_write()` method to filter instructions and return only external call instructions that are followed by instructions that update the contract’s storage.

{% hint style="info" %}
Python provides a built-in function called any(). It takes a list, set, or array and returns True if at least one value in the data structure evaluates to True.
{% endhint %}

{% hint style="info" %}
With Glider, you can call a method on a list of items, and that method will automatically be applied to each item in the list. This makes it easy to perform operations on multiple items at once. For example, the following code will return an array of function names:

```python
func_names = Functions().exec(4).name
print(func_names)
```
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/NUSps4CL](https://glide.r.xyz/query/NUSps4CL)

</details>



## **Exercise #4 - External Calls invoking abi.encode**

So far, our query identifies external calls and checks if any of the following instructions write to storage.

In this final exercise, we want to take it a step further by identifying external call instructions that also invoke **abi.encode**. To achieve this, you’ll need to add an additional filter to your query that checks for cases where the external call instruction includes a call to **abi.encode**.

{% hint style="info" %}
To retrieve all the calls made within an instruction, use the [callee\_names()](https://glide.gitbook.io/main/glider-ide/api/instruction/instruction.callee_names) function.
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/Y65j8PWM](https://glide.r.xyz/query/Y65j8PWM)

</details>



## Bonus Challenge

{% hint style="info" %}
Although we have not discussed what an instruction is yet, think of it as a line of code in a function.
{% endhint %}

We have a query that finds Solidity instructions:

```python
from glider import *

def query():
    return (
        Instructions()
        .exec(10)
    )
```

We want to update this query to find delegatecall instructions.&#x20;

**Challenge**: Identify the Glider function that, when called on `Instructions()`, will return only delegatecall instructions.

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/o3Q0dKq4](https://glide.r.xyz/query/o3Q0dKq4)

</details>

