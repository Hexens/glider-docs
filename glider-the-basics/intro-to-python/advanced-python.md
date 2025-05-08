# Advanced Python

## Classes

### What is a Class

In Python, a class is a way to group related code together, making it easier to work with complex data. While we won’t be creating our own classes in this tutorial, we do need to understand how to use them.

Many built-in features in Glider queries rely on classes. To use Glider classes, we:

* Create an instance of the class.
* Call methods (aka functions) on that instance to perform actions.

{% hint style="info" %}
**Note**: Although methods and functions have minor differences in Python, for the purposes of this series, we will use the terms interchangeably.
{% endhint %}

### How to Create a Class Instance

A class instance is a representation of a class that allows us to access its methods.

To create a class instance, use the class name followed by parentheses `()`:

```python
Functions()
```

### How to Call a Class Instance Method

To call a class method, we call the method after creating the class instance.

For example, the code below calls the Functions class' with\_name() function:

```python
Functions().with_name("swap")
```

This allows us to interact with Glider API class functions.

### Class Exercise

**Challenge**: Identify every class instance created in the following code:

```python
def query():
    Functions().with_name("swap").exec(10)
    
    Instructions().delegate_calls().exec(10)
    
    Contracts().with_struct_name("Order").exec(1337)    
```

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

The following class instances are created in the query above:

* Functions
* Instructions
* Contracts

</details>

## Glider API Methods

When writing a Glider query, Glider provides additional classes and class methods that are built-in and ready for use. These class methods power a Glider query and are essential for querying Solidity code.

If we refer back to our foundational query, we see the following code:

```python
Functions().with_name("swap").exec(10)
```

In this example, we are calling two Glider API functions:

* **with\_name("swap")** → A predefined method that queries for functions named "swap".
* **exec(10)** → A predefined method that executes the query and returns 10 results.

These built-in methods make it easier to write powerful and easy-to-understand Glider queries.

{% hint style="info" %}
The [Glider API documentation](https://glide.gitbook.io/main/api) is a valuable resource for understanding and utilizing Glider’s API methods. It offers detailed explanations, practical code examples, and a complete reference to the available classes and their methods, making it easier to integrate and work with the API effectively.
{% endhint %}

## Lists

In Python, lists allow us to store multiple values within a single variable. They are a fundamental data structure used frequently in Python and in Glider.

#### **What Do Lists Look Like?**

A list is defined using square brackets \[] and can contain multiple elements, such as strings, numbers, or objects. Here’s an example of a list containing three strings:

```python
["swap", "swapEth", "swapToken"]
```

As mentioned earlier, lists are not limited to storing strings. In Glider, lists are commonly used to store query results. For instance, if we run the following code:

```python
Functions().with_name("swap").exec(10)
```

Glider will return a list of function objects that match the query:

```python
[
    <api.functions.Function object at 0x7a887c3ae240>, 
    <api.functions.Function object at 0x7a887c82cf20>, 
    <api.functions.Function object at 0x7a887bca48f0>, 
    <api.functions.Function object at 0x7a887bca4140>
]
```

Each object in this list represents a Solidity function Glider found based on the search criteria. Lists like this make it easy to iterate over and process multiple query results efficiently.

{% hint style="info" %}
**Fact**: Although not covered in this tutorial series, there is another data type called sets, which is similar to lists. For the purposes of this series, we will use the terms interchangeably.
{% endhint %}

### Filtering Lists

One of the most common operations when working with lists is filtering, which helps remove unwanted items. This is especially useful for refining Glider query results by eliminating irrelevant data.

#### **Filtering with filter()**

The recommended way to filter items from a list is by using Glider's built-in filter() function. This function applies a filtering criterion to each item in the list and retains only those that meet the specified criteria.

Take a look at the example below, where we use filter() to filter out functions that aren't part of a specific address:

```python
functions.filter(only_uniswap_router)

def only_uniswap_router(function):
    return function.address() == "0x5C69bEe701ef814a2B6a3EDD4B1652CB9cc5aA6f"
```

Before diving into the criteria inside filter(), let’s quickly go over how filter works internally:

1. filter() iterates through each item in the list.
2. filter() applies the only\_swap\_functions to each item.
3. If the only\_swap\_functions returns True, the item remains in the filtered list.
4. If the only\_swap\_functions returns False, the item is removed.
5. A new list is returned, containing only the filtered items.

### The Filter argument

The next big question is: What goes inside the filter() parentheses?

In our example, we pass the only\_uniswap\_router function name into filter():

```python
functions.filter(only_uniswap_router)
```

This tells Glider to call only\_uniswap\_router on each item found. Note that we don't need to add the parenthesis after only\_uniswap\_router.

**What Does Passing only\_swap\_functions Do?**

By passing only\_uniswap\_router into filter(), we are instructing filter() to apply the only\_uniswap\_router function to each item in the list.

* If only\_uniswap\_router returns True, the item stays in the list.
* If only\_uniswap\_router returns False, the item is removed from the list.

This allows filter() to iterate through all items in the list, keeping those that meet the condition and discarding those that don’t.

### Refactoring Our Code

We can simplify the code by using a lambda function. With a lambda function, we can write the filter logic criteria like so:

```python
functions.filter(lambda function : function.address() == "0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045")
```

#### **Why Use a Lambda Function?**

* **More concise** - No need to define a separate function.
* **Quick one-liners** - Ideal for simple conditions.
* **Easier to read -** Filter logic is clear and compact.

#### **When to Use a Regular Function Instead?**

While lambda functions are great for short, simple filters, using a function is better when dealing with complex filtering logic that requires multiple conditions or other complex code.

## **Filtering Out Functions Exercise**

Now that we understand how filter() works, let’s apply it to an example where we want to filter out functions that lack if instructions.

```python
from glider import *

def query():
    swap_functions = Functions().with_name("swap").exec(10)
    return swap_functions
```

In the query above, we retrieve functions named “swap”. However, we want to remove functions from the functions list that do not contain if instructions.

To achieve this, we can use filter() to keep only functions that contain if instructions.

{% hint style="info" %}
**Hint**: To see if a function contains any if instructions, we can use the following code:

```
len(function.if_instructions().exec())
```
{% endhint %}

**Challenge**: Write a filter that will filter out functions that don't have if instructions.&#x20;

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/8fJwOAD7](https://glide.r.xyz/query/8fJwOAD7)

</details>

## Conclusion

Congratulations! 🎉&#x20;

Throughout this Python section, we’ve explored various Python features that will directly support your work in Glider. We started with the basics, such as creating variables and functions, and progressed to more advanced topics, like working with classes and filtering lists.

These concepts are essential for writing effective Glider queries. As we move into other sections, we’ll continue to refer back to the foundational query as a reference for building more complex Glider queries.

Now that we understand Glide queries from a Python-perspective, we will now focus on queries from a  Glider-perspective.

Let’s jump into the [Intro to Glider section ](../intro-to-glider.md)to get started!&#x20;
