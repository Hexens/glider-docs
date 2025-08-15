# Learning Instructions

## What are Instructions

Instructions can be thought of as individual lines of code within a function. They can include anything from an if statement or a function call to a return statement.

Instructions are the building blocks of Solidity contracts and represent the operations that the EVM (Ethereum Virtual Machine) will execute. This is why we refer to them as instructions.

## Finding Instructions

Let's start by running a simple query to find some instructions:

```python
from glider import *

def query():
    return Instructions().exec(3)
```

After running this query in the Glider IDE. You should find 3 instructions returned in the Output panel.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-07-25 at 3.35.51 PM.png" alt="" width="563"><figcaption><p>Glider IDE instruction output results</p></figcaption></figure>

## Foundational Instructions Query

Now that we understand what instructions are, let's walk through our second foundational query in this series, a Glider query designed to look for Solidity instructions that call Solidity's famous transferFrom function. Before we break down the query, let's identify the query goal.

### **Query Goal**

1. Find Solidity instructions that call the transferFrom() function - an ERC-20 function used to transfer tokens from one address to another.
2. Extract and inspect the arguments passed to each transferFrom() call.

The query can be found below:

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .with_callee_name("transferFrom")
        .exec(3)
    )

    instructions.filter(lambda instruction : print(instruction.get_value().get_args().expression))

    return instructions
```

## Breaking The Query Down

### Step 1 - Finding Instructions

In the first part of our query, we create an instance of the Instructions class:

```python
Instructions()
```

By initializing this class, we gain access to a variety of Instruction API methods provided by Glider. These methods allow us to further filter and query instructions programmatically.

{% hint style="info" %}
For a full list of available Instructions methods, refer to the [Glider API documentation](../../api/instructions/).
{% endhint %}

Next, we use the .with\_callee\_name() method, which allows us to locate instructions that contain function calls to transferFrom.

This method requires a single argument - the name of the function we want to search for. In our case, we pass "transferFrom" as a string:

<pre class="language-python"><code class="lang-python"><strong>.with_callee_name("transferFrom")
</strong></code></pre>

### Step 2 - Execute query

Now that we’ve defined a query to search for instructions that call transferFrom, we need to execute it. To do this, we call the .exec() method, which instructs Glider to run the query and return 3 results:

```python
.exec(3)
```

#### **Understanding exec()**

The .exec() method accepts two optional arguments:

* **Limit** – Specifies how many results Glider should return.
* **Offset (optional)** – Defines where Glider should start the search (useful for pagination).

In our case, we pass in 3 which tells Glider to return the first 3 results. The offset argument is optional so for now we ignore it.

{% hint style="info" %}
exec() returns a special type of list called [APIList](../../api/iterables/apilist.md). For now, we won’t focus on the differences between a Python List and APIList, as they won’t impact our use case in this series.
{% endhint %}

### Step 3 - Printing function call arguments

Now that we have our query results, we can extract additional info from our instructions. In this case, we want to analyze the arguments passed into the transferFrom function calls.

There are multiple ways to achieve this, but for this query, we use the [.filter() method](../../api/iterables/apilist.md#the-filter-function) provided by Glider.

#### **Using filter() to iterate through results**

We’ve previously discussed using filter to [iterate through results](../intro-to-glider.md#iterating-through-the-results) in an earlier section. Here, we’ll use filter again to iterate through our results.

The .filter() method accepts either a named function or a lambda function. In our query, we pass a lambda function to filter():

```python
lambda instruction : print(instruction.get_value().get_args().expression)
```

#### **Breaking Down the Lambda Function**

Inside the lambda function, we have the following code:

```python
print(instruction.get_value().get_args().expression)
```

Let’s break it down by ignoring print() for a moment and focusing on:

```python
instruction.get_value().get_args().expression
```

This expression retrieves the arguments passed to the transferFrom function from each instruction.

{% hint style="info" %}
**Tip**: An expression is a piece of code that returns a value when executed. Expressions can be written in many ways and can return different types of values. In our case, we are specifically interested in expressions that return True or False.
{% endhint %}

#### **What's exactly happening here?**

In our query, the instruction variable represents a single instruction from the instructions list. Using the instruction variable, we can apply a [method chain call](../intro-to-python/basic-python.md#chaining-function-calls) to execute a series of methods in sequence.

To extract the arguments passed into the transferFrom function, we call the following methods in sequence:

* **get\_value()** - Every instruction contains a value, which represents what the instruction is doing. There are different types of values. Since we are analyzing function calls, this method returns a value representing the transferFrom function call. We call a Call value.
* **get\_args()** - This method is called on the Call value returned by .get\_value(). get\_args() retrieves the list of arguments passed to the transferFrom function. &#x20;
* **expression** - This final call converts each argument into its source code representation, allowing us to see how the argument appears in Solidity.&#x20;

{% hint style="info" %}
**expression** is not a method, it’s a property. While the distinction between methods and properties goes beyond the scope of this series, it’s important to note that because **expression** is a property, we do not need to use parentheses () when calling it.

For example, instead of writing:

```python
instruction.get_value().get_args().expression()
```

We call it by:

```python
instruction.get_value().get_args().expression
```

This allows us to retrieve the source code representation of the argument directly.
{% endhint %}

#### **End Result**

When we check the final output, we see that the query returns an array representing the arguments passed into each transferFrom function call:

```python
"['_from', 'this', '_value']"
```

#### **Printing Output in the Glider IDE**

Glider IDE provides a useful Debug panel where we can print out query results for inspection. To take advantage of this feature, we use the standard print() function, which allows us to output any number of arguments directly to the Debug panel.

Since our query retrieves a list of function arguments, we can print them as follows:

```python
print(instruction.get_value().get_args().expression)
```

### **Step 4 - Returning the Results**

In the final step, we return the query results so they can be displayed in the Glider IDE Output panel.

Since the query() function is expected to return a list, we ensure it returns our filtered instructions query results (represented as a list):

```python
return instructions
```

## Query Results

Now that we’ve reviewed the query, let’s run it in the Glider IDE.

### **Running the Query**

Paste the following query into the Glider IDE, click "Run", and wait for the results:

```python
from glider import *

def query():
    instructions = (
        Instructions()
        .with_callee_name("transferFrom")
        .exec(3)
    )
  
    instructions.filter(lambda instruction : print(instruction.get_value().get_args().expression))

    return instructions
```

### **Interpreting the Results**

Once the query completes, Glider returns a series of instructions, each containing:

* The instruction source code
* The contract address for every instruction
* A printed list of transferFrom arguments from the results

Each instruction represents a call to the transferFrom function, and we can now view, in a structured and programmatic way, every argument that was passed into these function calls.

This demonstrates how Glider can efficiently and elegantly analyze function arguments within Solidity smart contracts.
