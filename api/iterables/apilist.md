# APIList

A `APIList` integrates classic list operations with advanced features. It allows functions to be applied to all elements, enables list refinement using `filter()` function, and includes a fallback mechanism to ensure default behavior when no transformations or filtering are applied.&#x20;

### APIList Functionality

A `APIList` supports all classic `list` operation, such as indexing, iteration, and length calculations. Functions called on the list are applied to every element, resulting a new `APIList` with the processed data.

### The `filter()` function

The `filter()` function uses a predicate to evaluate each element of the `APIList`. Elements where the predicate returns `true` are retained, while others are excluded, allowing precise control over the final list content.

### Flattening

When a function return another `APIList`, the results are flattened into a single, one-dimensional `APIList`. This ensures a unified list structure, facilitating easier processing and analysis.



### Functions that return APIList



* callables.exec()
* callable.callee\_values()
* callable.loops()
* [`functions.exec()`](../callables/functions/functions.exec.md)
* functions.list()
* [`function.properties()`](../callable/function/function.properties.md)
* modifiers.list()
* [`modifier.exec()`](../callables/modifiers/modifiers.exec.md)
* modifier.properties()
* instructions.exec()
* instructions.list()
* `instruction.get_dests()`
* [`instruction.next_block()`](../instruction/instruction.next_block.md)
* [`instruction.next_instruction()`](../instruction/instruction.next_instruction.md)
* [`instruction.exec()`](../instructions/instructions.exec.md)
* instruction.get\_components()
* breakinstruction.get\_block\_instructions()
* startassemblyinstruction.get\_block\_instructions()
* tryinstruction.get\_block\_instructions()
* [`call.get_args()`](../value/call/call.get_args.md)
* [`call.get_call_gas()`](../value/call/call.get_call_gas.md)
* [`call.get_call_salt()`](../value/call/call.get_call_salt.md)
* [`call.get_call_value()`](../value/call/call.get_call_value.md)
* [`value.get_arg_vars()`](../value/value/value.get_arg_vars.md)
* value.get\_callee\_values()
* [`value.get_global_vars()`](../value/value/value.get_global_vars.md)
* value.get\_local\_vars()
* [`value.get_state_vars()`](../value/value/value.get_state_vars.md)
* [`value.get_vars()`](../value/value/value.get_vars.md)
* tupleexpression.get\_components()
* value.expression.get\_components()
* value.get\_dests()
* varvalue.get\_defining\_points()
* point.df\_reaches\_from\_functions\_arguments()
* point.df\_reaching\_functions\_arguments()
* argumentpoint.list()
* argumentpoint.with\_memory\_type()
* argumentpoint.with\_name()
* argumentpoint.with\_type()
* argumentpoint.with\_type\_convertible()
* globalvariables.list()
* localvariables.list()
* localvariables.with\_memory\_type()
* localvariables.with\_type()
* statevariables.exec()
* statevariables.list()
* callnode.callees()
* callnode.callers()
* contract.get\_contracts\_from\_same\_src\_file()
* contracts().exec()
* enums.exec()
* errors.exec()
* events.exec()









