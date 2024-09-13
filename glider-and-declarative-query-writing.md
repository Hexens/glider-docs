# Glider and Declarative Query Writing

## Glider and Declarative Query Writing

Declarative programming is a style of coding where the developer describes what should be done rather than how it should be done. In declarative code, goals or results are expressed, while the details of execution are left to the system or runtime environment.

### Key Characteristics of Declarative Programming

* Focus on the Result: Instead of specifying a step-by-step process for completing a task, declarative programming focuses on what needs to be achieved.
* Minimal Explicit Steps: There is no need to describe all intermediate steps of the task; the system determines how to achieve the result on its own.

### Examples of Declarative Languages and Approaches

* SQL: The developer describes what data is needed but does not specify how the database should retrieve it.
* Functional Programming (e.g., Haskell): The developer describes functions and relationships between data without worrying about how they will be executed.
* CSS: The appearance of elements is described, but not how the browser applies these styles. Unlike imperative programming, the declarative style simplifies code, making it easier to write, more readable and easier to modify, especially in complex systems.

### Comparison of Declarative and Imperative Approaches

* Imperative and declarative approaches to programming differ in how they describe task execution. Here are the main differences between them:
* Approach to Describing a Solution:
* Imperative Approach: Focuses on how to perform a task, providing step-by-step instructions to achieve the result.
* Declarative Approach: Describes what needs to be done without specifying how it should be achieved.

#### Example

**Imperative (Python):**

```python
numbers = [1, 2, 3, 4, 5, 6]
evens = []
for number in numbers:
    if number % 2 == 0:
        evens.append(number)
print(evens)
```

Here, the steps are explicitly specified: create a list, iterate through each element, check if it is even, and add it to a new list.

**Declarative (Python, list comprehension):**

```python
numbers = [1, 2, 3, 4, 5, 6]
evens = [number for number in numbers if number % 2 == 0]
print(evens)
```

We simply specify that we want to get the even numbers from the list, without describing the process step by step. Readability and Code Maintenance: Imperative Approach: Can become complex to read and maintain as the number of steps and complexity of algorithms increase. Declarative Approach: Generally results in more concise, understandable code that is easier to maintain, as it only describes the goal. Level of Abstraction: Imperative Approach: Typically operates at a low level of abstraction, as it requires detailed description of each step, including managing the program's state. Declarative Approach: Operates at a higher level of abstraction, as it hides implementation details and focuses on the final goal. Now that we have covered what declarative coding is, its time to move on to Glider! Glider gives ability to mix declarative and imperative forms to write code queries. Before the release of Glider 1.0: As the user has filtered Contracts/Functions/Instructions, they received a list of objects they wanted. Then, using imperative methods (e.g., if, for, while), they iterated over these objects to write their query. This approach, while functional, has several drawbacks: Imperative code is more difficult to read and write. Due to the large number of nested loops and checks, it becomes hard to comprehend. There is a significant amount of duplicated code. Recognizing these issues, the approach to writing queries in Glider 1.0 was completely revised, and it now aligns more closely with the declarative style of programming.

### What Was Changed?

Now, the functions of most Glider 1.0 classes return not standard lists, sets, or tuples, but new objects of the `APIList`/`APISet`/`APITuple` classes. What is useful about these classes? Lets examine the difference using the example of a query to find reentrancy vulnerabilities in ERC777.

**A query without using the declarative approach looks as follows:**

```python
from glider import *
def query():
    """
    @title: ERC777 reentrancy.
    @description: The query is designed to find ERC777 reentrancy bugs in contracts, the pattern looks like this.
    @author: Hexens team.
    @tags: reentrancy, erc777, read-only reentrancy, bridge
    @references: https://github.com/Hexens/Smart-Contract-Review-Public-Reports/blob/main/Hexens_Polygon_zkEVM_PUBLIC_27.02.23.pdf
    """
    instructions = (
        Functions() # we iterate over all functions
        .with_one_property([MethodProp.PUBLIC, MethodProp.EXTERNAL]) # filter only public and external
        .without_modifier_names(['nonReentrant', 'lock', 'onlyOwner']) # filter out the ones with these modifiers
        .with_arg_type('address') # has an argument of type address
        .instructions() # level-down to the instructions of the filtered functions
        .with_callee_function_name('balanceOf') # take the instructions that have a balanceOf call
        .exec(3000)) # limit the result to the first 3000
    results = [] # prepare a list that will include the results
    for ins in instructions: # iterate over all of the instructions we got
        for second in ins.next_instruction(): # take all of the instructions that come after our balanceOf instruction in the CFG graph
            if second.is_call() and ('transferFrom' in second.callee_names() or 'safeTransferFrom' in second.callee_names()):
                for third in second.next_instruction(): # take all the instructions that come after the transferFrom
                    if third.is_call() and 'balanceOf' in third.callee_names(): # check that we have a balanceOf once more
                        results.append(ins) # append to the resulting set
                        break
    return results
```

In this query, the declarative part is only the fragment where we find all `instructions` with the function call `transferFrom`. Additionally, the function where `transferFrom` is called must be `public` or `external`, one of its arguments must be of type `address`, and it should not contain the modifiers `nonReentrant`, `lock`, or `onlyOwner`. After we find the corresponding `instructions`, we use a `for` loop to iterate through them and, using the `next_instruction()` function, obtain the next instruction after the `balanceOf` call. We then check if this `instruction` contains a call to the `transferFrom` or `safeTransferFrom` function. If such a call is present, we move to the next instruction after the `transferFrom`/`safeTransferFrom` call and check if the `balanceOf` function is called there. If so, we have found the required contracts. We add such `instructions` to the result list and return it. The entire code for this query takes around 40 lines, uses 3 for loops, and creates one result list.

**Now let's look at the new syntax in Glider 1.0 for declarative query writing. The logic of the query will remain unchanged:**

```python
from glider import *
def query():
    instructions = (
        Functions()
        .with_one_property([MethodProp.PUBLIC, MethodProp.EXTERNAL])
        .without_modifier_names(['nonReentrant', 'lock', 'onlyOwner'])
        .with_arg_type("address")
        .instructions()
        .with_callee_function_name('balanceOf').exec(3000)
        .next_instruction()
        .filter(lambda x: "transferFrom" in x.callee_names() or 'safeTransferFrom' in x.callee_names())
        .next_instruction()
        .filter(lambda x: "balanceOf" in x.callee_names())
    )
    return instructions
```

The first thing that stands out is the noticeable reduction in the amount of code compared to the initial query. Lets explore how it works! The first part, where we retrieve the necessary `instructions`, remains the same as in the previous query. However, next, we use the `next_instruction` function, which is only available for objects of type `Instruction`. How is this possible? In Glider Engine, after calling the `exec()` function, you get a `list` of objects depending on the type of the object on which the `exec()` method was called. For example, when `exec()` is called on an object of type `Instructions`, the function will return an `APIList[Instruction]`, whereas in the previous version of Glider, it would have returned a `List[Instruction]`. What is the difference between `APIList[type]` and `List[type]`? `APIList[type]` allows you to apply a method not to the entire `list` at once, but to each individual element. Therefore, we can call the `next_instruction` method, which is defined for `Instruction`, on the entire list of `instructions` without using a `for` loop. One of the key features of the `APIList[type]`, `APISet[type]`, and `APITuple[type]` structures is their unidimensionality. This means that when calling the `next_instructions` function, which returns an `APIList[Instruction]`, the result will be a one-dimensional `APIList`. In other words, the lists returned from the called functions maintain the same type of structure `APIList`, `APISet`, or `APITuple` with which we started working. This makes possible of chaining functions/properties on list, as with other declarative parts. This feature has its pros and cons. The advantage is that we always know exactly what type of data we are dealing with. However, the downside is that sometimes, due to this feature, it may be necessary to use traditional imperative approaches. For example, if you need to filter the list returned by the `next_instructions` function and select the original instructions based on checks, this might require breaking the query chain and using loops. It is important to note that after calling such a method, all objects in `APIList[Instruction]` will be modified. In our case, `APIList[Instruction]` will contain all subsequent instructions for the instructions obtained in the first part of our query. What does this give us? The ability to write queries this way allows for more compact and readable queries, as seen in the examples. One of the significant updates is the `filter()` function, which also supports better chaining list filtering during query writing. The `filter()` function is a higher-order function that takes another function as an argument. The function passed to `filter()` must be a `predicate function`, meaning it should return a `boolean` value (`true` or `false`). This requirement ensures more explicit query behavior. The `filter()` function allows the following: if the predicate function passed to `filter()` returns `true`, the object from `APIList[type]` will remain in the list; if `false`, the object will be removed. This helps eliminate if statements, making queries shorter and more readable. Let's examine the use of the `filter()` function with an example. In the declarative query, the first call to `filter()` received a predicate `lambda function`: `lambda x: "transferFrom" in x.callee_names() or 'safeTransferFrom' in x.callee_names()`. As an argument, this `lambda function` automatically receives an `instruction` from the `APIList[Instruction]` list. If the `lambda function` returns `true`, the `instruction` remains in the `APIList[Instruction]`; if `false`, it is removed. As a result, the length of the query code is 12 lines. This query does not use for loops or if statements, and no separate result list is created. The readability of the query has significantly increased, and the process of writing it has become simpler.
