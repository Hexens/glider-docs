---
description: This page describes what are the main concepts of writing glides
---

# 🏄 Writing Glides

A glide code can be separated into two parts: declarative queries (also called online part) and imperative arbitrary logic part (offline part)

Imagine the following glide code:

```python
def query(): # The name query() is constant, and should not be changed
  # Querying the DB in declarative manner
  instructions = Functions()\
  .with_one_property([MethodProp.EXTERNAL, MethodProp.PUBLIC])\
  .without_properties([MethodProp.HAS_MODIFIERS, MethodProp.IS_CONSTRUCTOR])\
  .instructions()\
  .with_callee_function_name('selfdestruct')\
  .exec() # chain of calls must always end with exec() otherwise the query will not be dispatched
  
  # Arbitrary logic part, where we analyse the CFG/DFG graphs to filter the result
  results =[]
  for i in instructions: # iterate over instructions that we got from query
    if i.has_global_df(): # check that the instruction has a dataflow from global vars
    # such as msg.sender, tx.origin, function arguments etc..
    # basically we want to check that the selfdestruct's param is controllable by the caller
      
      # use a variable to mark whether the instruction should be included in the result or not
      flag = True 
      # previous_instructions will return all of the instruction that come before in the CFG (control flow graph)
      for prev in i.previous_instructions():
        #check if its a function call of "if" and that it does not include msg.sender in the expression
        if (prev.is_call() or prev.is_if()) and 'msg.sender' in prev.source_code():
          flag = False
          break
      # include the instruction in the resulting set
      if flag:
        results.append(i)

  return results # to see the results the query() function must return a list of objects
```

## Code as data

Glider compiles and constructs artefacts from source code and places them in a specialized high-performance database.

This gives the ability for query writers to query code as data in a declarative format using Glider's [API](https://app.gitbook.com/o/D7bVwvgIhKRqv3dZQbQH/s/KRI4GLnp45wDq2xrEWyI/)

The code partinstructions = Functions()\\

```python
 instructions = Functions()\
  .with_one_property([MethodProp.EXTERNAL, MethodProp.PUBLIC])\
  .without_properties([MethodProp.HAS_MODIFIERS, MethodProp.IS_CONSTRUCTOR])\
  .instructions()\
  .with_called_function_name('selfdestruct')\
  .exec()
```

showcases the declarative part of the glide, where we use `api.Functions` class to iterate over all of the functions and filter them, then we continue the chain and "level-down" to the instructions of already filtered functions, and then we filter the instructions.&#x20;

_Note that the query chain always ends with_ [_`exec()`_](https://app.gitbook.com/s/KRI4GLnp45wDq2xrEWyI/instructions/instructions.exec) _call._ &#x20;

## Arbitrary logic (CFG/DFG/Taint analysis)

Glider leverages the Python environment to give users the possibility to write arbitrary logic on the data received from DB.

```python
  # Arbitrary logic part, where we analyse the CFG/DFG graphs to filter the result
  results =[]
  for i in instructions: # iterate over instructions that we got from query
    if i.has_global_df(): # check that the instruction has a dataflow from global vars
    # such as msg.sender, tx.origin, function arguments etc..
    # basically we want to check that the selfdestruct's param is controllable by the caller
      
      # use a variable to mark whether the instruction should be included in the result or not
      flag = True 
      # previous_instructions will return all of the instruction that come before in the CFG (control flow graph)
      for prev in i.previous_instructions():
        #check if its a function call of "if" and that it does not include msg.sender in the expression
        if (prev.is_call() or prev.is_if()) and 'msg.sender' in prev.procedure_graph_node.expression:
          flag = False
          break
      # include the instruction in the resulting set
      if flag:
        results.append(i)
```

As you can see we use here basic Python constructs and Glider's functionality to do quite complex filtering on the result.&#x20;

We check that the instruction we got has a global dataflow (controllable by the caller) and that there is no function call or "if"s containing msg.sender that precedes the selfdestruct call.&#x20;

This is a playbook example of a query, while it already can yield very good results, the query has a lot of room for improvement, e.g. instead of checking `msg.sender` to not be part of the expression one should check that the call/if expressions are not tainted from msg.sender.

Users can combine declarative and imperative logic in any order and number.

## Returning results

In order to see the results, the query() function must return a list of objects, the types of objects supported for return right now are [Contract](https://app.gitbook.com/s/KRI4GLnp45wDq2xrEWyI/contract), [Function](https://app.gitbook.com/s/KRI4GLnp45wDq2xrEWyI/function), [Modifier](https://app.gitbook.com/s/KRI4GLnp45wDq2xrEWyI/modifier), and [Instruction](https://app.gitbook.com/s/KRI4GLnp45wDq2xrEWyI/instruction).&#x20;

## Experimental feature - print()

Glider has an experimental feature to show you print() outputs that you would place in the query code. This is mainly useful while debugging the query code. Whatever Glider prints during the execution will be aggregated and shown as the last output root in the output (right) window.

Note that the feature is experimental and may be removed in future.

Example:

```python
      for prev in i.previous_instructions():
        if (prev.is_call() or prev.is_if()) and 'msg.sender' in prev.procedure_graph_node.expression:
          flag = False
          print(prev.solidity_callee_names()) # add this line to the code
          break
```

Output:

```json
{
  "print_output": [
    "['require']",
    "[]",
    "[]",
    "[]",
    "[]",
    "['require']",
    "[]",
    "['require']",
    "['require']",
    "['require']",
    "['require']",
    "['require']",
    ...
  ]
}
```

## from glider import \*

In the Glider's web interface, the queries will usually start with&#x20;

```python
from glider import *
```

{% hint style="info" %}
While this will not affect the execution of the query in any way, and this line can be skipped, it is used for the query editor interface to activate the Intellisense with autocomplete, tooltips, and other features.
{% endhint %}
