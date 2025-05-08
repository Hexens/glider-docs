# Learning Functions

## What are Functions

In Solidity, functions are blocks of re-usable code that can be used by contracts to execute one or more instructions. Functions can be called by other contracts or be called internally within the same contract.

## Finding Functions

We can identify Solidity functions through the use of the Functions() class. Let's see this in action by running the following query below:

```python
from glider import *

def query():
    return Functions().exec(10) 
```

As you can see in the results of the Output panel, Glider has returned us 10 functions.

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-09 at 2.15.34 PM.png" alt="" width="375"><figcaption><p>Glider IDE function output results</p></figcaption></figure>

{% hint style="info" %}
The Glider Functions class inherits from the Callables class, which provides various methods for querying Solidity functions. Although we won’t delve into inheritance here, just know that any method available to a Callables instance can be used interchangeably with a Functions instance.
{% endhint %}

## Foundational Functions Query

In this section, we’ll explore a foundational query designed to find Solidity functions that searches for functions that call the ECDSA.recover function.

### **Query Goal**

We want to identify functions named "castVoteBySig" that call OpenZeppelin’s ECDSA.recover function. In this query, we assume that any function that calls a function named "recover" is utilizing the ECDSA library.

To achieve this, our query will:

1\. Search for functions named "castVoteBySig".

2\. Filter functions that contain a call to "recover", assuming it’s from the ECDSA library.

### **Query Code**

```python
from glider import *

def query():
    functions = (
        Functions()
        .with_name("castVoteBySig")
        .exec(100)
        .filter(lambda function : "recover" in function.callee_values().name)
    )
 
    return functions
```

Now let’s break down this query step by step.

### Step 1 - Finding the castVoteBySig Functions

The first step in our query is to find functions named castByVoteSig. To do this, we create an instance of the Functions class:

```python
Functions()
```

By creating this class instance, we gain access to Glider API methods that allow us to filter and retrieve functions found via Glider.

**Using .with\_name() to Find Functions by Name**

With our Functions class instance, we can now call the .with\_name() method to search for functions with a specific name. Since we are looking for castVoteBySig functions, we pass this name as an argument:

```python
.with_name("castVoteBySig")
```

#### **Executing the Query with .exec()**

To run the query, we call .exec(), which executes the query. As discussed in the [Learning Instructions section](../instructions/learning-instructions.md#breaking-query-down), exec() requires an integer argument specifying the maximum number of results to return.

In this case, we pass 100, meaning we want to retrieve up to 100 results:&#x20;

```python
.exec(100)
```

#### **Putting It All Together**

When combined, our query so far looks like this:

```python
Functions()
    .with_name("castVoteBySig")
    .exec(100)
```

This ensures that we return up to 100 Solidity functions named castVoteBySig, setting us up for the next step, filtering functions that call the recover function.

### **Step 2 - Filtering functions via calls to recover()**

Now that we have found functions named castVoteBySig, we need to filter the results further to only include functions that call ECDSA.recover.

To achieve this, we use the .filter() method, which allows us to exclude any functions that do not meet our criteria.

#### **Applying the Filter**

We call .filter() and pass in a lambda function that checks if recover() is present in the callee function names of each result:

```python
.filter(lambda function : "recover" in function.callee_values().name)
```

#### **Breaking Down the Filter Condition**

Inside of filter, we provide a lambda function that contains the filter criteria:

```python
"recover" in function.callee_values().name
```

The code can be broken down as follows:

* **function.callee\_values()** - Retrieves a list of functions that the current function calls.
* **.name** - Extracts the functions names from the list of function calls.
* **"recover" in function.callee\_values().name** - Checks if "recover" is among the called function names lists. Returns True if recover is in the list. False if not.

If the expression returns True, then the function will be kept. If the expression returns False, then the function will be discarded from the list.

#### **The Query as a Whole**

Here our query put together looks like:

```python
Functions()
    .with_name("castVoteBySig")
    .exec(100)
    .filter(lambda function: "recover" in function.callee_values().name)
```

## Query Results

### **Running the Query**

Now that we’ve covered the query, let’s run it in Glider IDE. Paste the following query into the Glider IDE, click "Run", and wait for the results:

```python
from glider import *

def query():
    functions = (
        Functions()
        .with_name("castVoteBySig")
        .exec(100)
        .filter(lambda function : "recover" in function.callee_values().name)
    )
 
    return functions
```

### **Interpreting the Results**

Once the query completes, Glider returns a list of functions and their contract addresses. Each function in the results:

* Is named castVoteBySig, as specified in our query.
* Contains a call to ECDSA.recover(), confirming our filtering logic worked correctly.
* Includes the function’s Solidity source code, allowing us to inspect its implementation.

With this query, we efficiently identify functions that match castVoteBySig and interact with OpenZeppelin’s ECDSA.recover(). This allows us to review relevant results gaining valuable insights into how these functions are implemented and used.
