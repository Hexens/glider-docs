# Basic Python

## The Foundational Query

Glider queries are powered by Python, a high-level programming language known for its simplicity and readability. If you’re new to Python, this section will introduce you to core concepts such as variables and functions. Along the way we will show you Python is used to write Glider queries.

In the following topics below, we’ll analyze our foundational query, discovering essential Python functionalities used throughout the query. If you’re unfamiliar with Python, you can refer to this query as a guide to understanding how different aspects of the language work.

The first foundational query we will review can be found below:

```python
from glider import *

def query():
    swap_functions = Functions().with_name("swap").exec(10)

    swap_functions.filter(lambda function: print(function.address()))

    return swap_functions
```

## Variables

In Python, variables allow you to store and manage data, such as strings, integers, and more. They act as placeholders for values that you can reference later in your code.

For example, consider the following code:

<pre class="language-python"><code class="lang-python"><strong>swap_functions = Functions().with_name("swap").exec(10)
</strong></code></pre>

Here, we are creating a variable called `swap_functions`. The variable name is on the left side of the equals = operator, while the right side contains the data the variable stores.

In this case, the data consists of the query results for the first 10 "swap" functions.

```python
Functions().with_name("swap").exec(10)
```

### **Naming Variables**

You can name variables however you like, but it’s best to choose a name that clearly describes what the variable stores. In this case, since the variable holds queried functions, we name the variable `swap_functions` to keep the code clear and readable.

Once created, a variable can be reused throughout the query, making the code more elegant and easy to read.

### Variable Exercise

**Exercise**: Create a variable that stores the number of functions found in the `swap_functions` variable.

{% hint style="info" %}
**Hint**: You can use Python’s built-in len() function to count the number of items in a variable.
{% endhint %}

```python
from glider import *

def query():
    swap_functions = Functions().with_name("swap").exec(10)

    # CHALLENGE: Create a variable and assign it to len(swap_functions)

    swap_functions.filter(lambda function : print(function.address()))

    return swap_functions
```

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/BOTP5BqCh](https://glide.r.xyz/query/BOTP5BqCh)

</details>

## Strings, Integers, and Booleans

### Strings

In Python, text is often enclosed in double quotes " " like this:

```python
"This is a string"
```

This is called a string - a data type used to store text. Strings have many uses, but in Glider queries, they play a key role in specifying how a query should be executed.

For example, when searching for functions by name, we use a string to specify the function name we want to find:

```python
Functions().with_name("swap")
```

In the code above, we have the "swap" string which tells Glider we want to find functions named "swap."&#x20;

### Integers

In programming, we often work with numbers. In Python, these are called integers.

Glider queries use integers to specify how many records Glider should search for. If we look back at our foundational query, we can see an integer written in the exec() call:

```python
Functions().with_name("swap").exec(10)
```

Here, the integer 10 tells Glider to fetch 10 matching functions.

### Booleans

In Python, a boolean (bool) is a data type that represents either a True or False value. Certain Python code can return booleans. Booleans are useful for making decisions in code, such as filtering results in a Glider query.&#x20;

Let’s look at some examples. In the code below, the statement returns True because both strings are identical:

```python
"onERC721Received" == "onERC721Received" # Returns True
```

If the strings were different, the expression would return False.

```python
"onERC721Received" == "receivedERCToken" # Returns False
```

{% hint style="info" %}
**Tip**: An **expression** is code that returns a value. A **value** is a piece of data that can be a string, integer, boolean, etc.

```python
"onERC721Received" == "receivedERCToken"
```

The code shown above is an expression since it returns return True or False. An expression can return more than just True or False; it can return strings, integers, etc.
{% endhint %}

## Functions

In Python, we often find ourselves writing the same code multiple times. This can make our programs long, repetitive, and difficult to understand. A great way to solve this is by using functions.

A function is a reusable block of code that helps keep our programs organized and clean. Python and Glider provide many built-in functions, but we can also create our own! &#x20;

Let’s look at the following function:

```python
def contains_state_variables(contract):
    return len(contract.state_variables().exec()) > 0
```

This function contains a single line of code that checks whether a contract contains any state variables.&#x20;

Once we create a function, we can then run the function (aka execute the function code). With a function, our code becomes smaller and simpler to understand. To use (or call) this function, we write:

```python
creates_local_variables(function)
```

In this section, we will go over various aspects of functions, how to create them, and conclude with an challenge exercise.

{% hint style="info" %}
**Tip**: In Python, functions are sometimes called methods. While there’s a difference between the two, for this series, we’ll use "functions" to refer to both.
{% endhint %}

### Why Use Functions

When we write code, we often reuse the same logic multiple times or find ourselves grouping chunks of code together. Let’s consider the following Glider query:

```python
Functions()
    .exec(1000)
    .filter(lambda function : function.get_contract().name not in {"UniswapV3Pool"})
    .filter(
        lambda function : 
        len(
            function
            .instructions_recursive()
            .filter(lambda instruction: instruction.is_if() or instruction.is_if_loop() or instruction.is_start_loop())
        ) > 30
    )
```

Even without understanding exactly how this code works, it’s clear that a lot is happening. Can we improve the readability of this query? Yes! By using functions, we can simplify the query as follows:

```python
(
    Functions()
    .exec(1000)
    .filter(not_uniswap_pools)
    .filter(has_too_much_control_flow)
)

def not_uniswap_pools(function):
    return function.get_contract().name not in ["UniswapV3Pool"]
 
def has_too_much_control_flow(function):
    return len(
        function
        .instructions_recursive()
        .filter(is_control_flow)
    ) > 30

def is_control_flow(instruction):
    return instruction.is_if() or instruction.is_if_loop() or instruction.is_start_loop()
```

In this updated version, we’ve extracted parts of the query into separate functions. This makes the code more readable by clearly defining what each section of code does. Now, if we look at the main portion of the query:

```python
(
    Functions()
    .exec(1000)
    .filter(not_uniswap_pools)
    .filter(has_too_much_control_flow)
)
```

We can easily understand it at a glance. Roughly translated, it means:

> Find 1000 functions that are not part of a Uniswap pool and has too much control flow.

By creating functions, we’ve written cleaner, more readable code that is easier to maintain and understand.

### Function Name

A function name describes what the function does. Choosing a clear and meaningful name makes your code easier to read and understand.

For example, if we create a function to find contracts named IERC20, we might call the function get\_erc20\_interface\_contracts as seen below:

```python
def get_erc20_interface_contracts():
```

Each function name must be unique, and we use the name to call (run) the function later. We can identify the function name by looking at the text that comes after the def keyword:

```python
def defines_variables():
```

This function name gives us an idea of what the function does and hints at what it might return (more on that soon!).

### Returning Data from Functions

Functions don’t just execute code - they can also return data. This is useful when we want a function to perform a task and then provide a result we can use elsewhere.

{% hint style="info" %}
**Tip**: Functions are not required to return data.
{% endhint %}

In fact, every Glider query relies on return values! For example, the query() function below returns the Glider query results:&#x20;

```python
def query():
    swap_functions = Functions().with_name("swap").exec(10)
    
    # Return the Glider results
    return swap_functions
```

By returning values, functions become powerful tools for organizing and reusing code efficiently. This allows us to break down complex logic into smaller, more manageable pieces.

### Function Arguments

When writing functions, we often need to use data from outside the function inside of the function. This is where function arguments come in.

A function argument allows us to pass additional data into a function so it knows exactly what to do.

#### **What do function arguments look like?**

Function arguments are placed inside parentheses `()` when defining a function. For example, the function below accepts a single argument named `contract`:

```python
def contains_state_variables(contract):
    return len(contract.state_variables().exec()) > 0
```

Inside the function, we can use the function argument just like any other variable.

Functions can also accept multiple arguments like so:

```python
def contains_state_variables(contract, state_variables_count):
    return len(contract.state_variables().exec()) > state_variables_count
```

In this example, we introduced a second argument, `state_variables_count`, which we then use to gauge how many state variables the contract has. &#x20;

Using function arguments makes our functions more flexible and reusable, allowing us to work with different data each time we call the function.

### How to Create Functions

Now that we’ve covered the basics of functions, let’s learn how to create one. In Python, we use specific keywords and syntax to define a function.

Here’s a simple function template:

```python
def name_of_function(argument_1, argument_2):
    # ADD CODE HERE
```

#### **Breaking it Down**

In the function above we:

* Defined a function using the `def` keyword.
* Named the function `name_of_function`.
* Added two arguments inside the parentheses `(argument_1, argument_2)`.
* Add code inside of the function. Be sure to indent the code inside the function, otherwise the code won't execute.

This template can be used whenever you want to create a function. Now, let’s explore how to call and use our functions!&#x20;

### Calling Functions

Once we define a function, we need to call it to execute its code.

To call a function, simply write the function name followed by parentheses `()`:

```python
if_instructions()
```

This calls a function named **if\_instructions**.

#### **Calling Functions with Arguments**

If a function requires arguments, we need to add the arguments inside the parentheses.

For example, the with\_name() function accepts a single argument:

```python
with_name("swap")
```

Here, we pass the string "swap" into the with\_name() function. This tells with\_name() we want to find functions named swap.

Calling functions allows us to run reusable code and pass in custom values when needed.

### Chaining Function Calls

A useful feature in Python is chaining function calls, which allows us to call multiple functions back to back. But what does this actually do, and why use it?

#### **How It Works**

When we chain function calls, each function returns data that the next function uses. This makes our code more concise and readable.

For example, consider this Glider query:

```python
Functions().with_name("swap").exec(10)
```

#### **Breaking It Down**

Let's now break down the code snippet into sections:

* `Functions()` → Creates a Functions class instance. **Note**: We'll discuss class instances more in the [Advanced Python section](advanced-python.md#how-to-create-a-class-instance).
* `.with_name("swap")` → Calls the with\_name() function on the Functions object to query for functions named "swap", returning a Functions object.
* `.exec(10)` → Calls the exec() function on the Functions object to execute the query and return 10 results.

By chaining these function calls together, we can apply multiple operations in a single statement. This makes the code cleaner, more readable, and more efficient.

{% hint style="info" %}
You can wrap chained function calls in parentheses `()` to make the code easier to read:

```python
(
    Functions()
    .with_name("swap")
    .exec(10)
)
```
{% endhint %}

### Using print() in Glider queries for debugging

One of the most useful functions in Glider queries is print(). It can take any number or type of arguments. When called, print() prints the arguments to the Output Panel in the Glider IDE.

For example running the following code below:&#x20;

<pre class="language-python"><code class="lang-python"><strong>print("Check out this cool info!")
</strong></code></pre>

Will display in following content in the Glider IDE Output panel:

```
Check out this cool info!
```

<figure><img src="../../.gitbook/assets/first (1).gif" alt=""><figcaption><p>Printing Output to the Glider IDE</p></figcaption></figure>

#### **Why Use print()?**

The print() function is great for:

* View what a variable stores.
* Check if a section is executed (if it's printed, you know the code is executed)

## Printing Function Properties Exercise

**Challenge**: Modify the query below by adding the print() function to display the function properties of the `swap_function` variable in the Glider IDE output panel.

{% hint style="info" %}
**Hint**: To determine the function properties, we can call:

```python
function.properties()
```
{% endhint %}

```python
from glider import *

def query():
    swap_functions = Functions().with_name("swap").exec(10)

    swap_function = swap_functions[0]
    
    # CHALLENGE: Print the swap_function properties below

    return swap_functions
```

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/aGtCqO1E](https://glide.r.xyz/query/aGtCqO1E)

</details>

## Conclusion

Great job! 🎉&#x20;

You’ve now learned some of the fundamental building blocks of Python, including:

* **Variables** - How to store and reuse data.
* S**trings, Integers, and Booleans** - The different types of data you can work with.
* **Functions** - How to create reusable blocks of code and run functions.
* **Chaining function calls** - How to streamline your Glider queries by calling multiple functions back-to-back.
* **The print() function** - A useful function for debugging and checking values inside your queries.

### **What’s Next?**

In the [next section](advanced-python.md), we’ll dive into more complex concepts including:

* **Classes** - Understanding how to create class instances.
* **Glider API Functions** - Exploring built-in functions provided by Glider.
* **Lists** - Understanding and efficiently managing Glider query results.

Keep going as you’re on your way to mastering Python for Glider queries!
