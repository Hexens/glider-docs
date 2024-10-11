# APIList

A `APIList` integrates classic list operations with advanced features. It allows functions to be applied to all elements, enables list refinement using `filter()` function, and includes a fallback mechanism to ensure default behavior when no transformations or filtering are applied.&#x20;

### APIList Functionality

A `APIList` supports all classic `list` operation, such as indexing, iteration, and length calculations. Functions called on the list are applied to every element, resulting a new `APIList` with the processed data.

### The `filter()` function

The `filter()` function uses a predicate to evaluate each element of the `APIList`. Elements where the predicate returns `true` are retained, while others are excluded, allowing precise control over the final list content.

### Flattening

When a function return another `APIList`, the results are flattened into a single, one-dimensional `APIList`. This ensures a unified list structure, facilitating easier processing and analysis.



### Functions that return APIList

* [`function.callee_values()`](../callable/callable.callee\_values.md)
* [`function.properties()`](../callable/function/function.properties.md)
* [`functions.exec()`](../callables/functions/functions.exec.md)
* [`modifier.exec()`](../callables/modifiers/modifiers.exec.md)
* [`instruction.get_dest()`](../instruction/instruction.get\_dest.md)
* [`instruction.next_block()`](../instruction/instruction.next\_block.md)
* [`instruction.next_instruction()`](../instruction/instruction.next\_instruction.md)
* [`instruction.exec()`](../instructions/instructions.exec.md)
* [`call.get_args()`](../value/call/call.get\_args.md)
* [`call.get_call_gas()`](../value/call/call.get\_call\_gas.md)
* [`call.get_call_salt()`](../value/call/call.get\_call\_salt.md)
* [`call.get_call_value()`](../value/call/call.get\_call\_value.md)
* [`value.get_arg_vars()`](../value/value/value.get\_arg\_vars.md)
* [`value.get_global_vars()`](../value/value/value.get\_global\_vars.md)
* [`value.get_state_vars()`](../value/value/value.get\_state\_vars.md)
* [`value.get_vars()`](../value/value/value.get\_vars.md)

