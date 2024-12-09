# APISet

A `APISet` integrates classic set operations with advanced features. It allows functions to be applied to all elements, enables set refinement using the `filter()` function, and includes a fallback mechanism to ensure default behavior when no transformations or filtering are applied.

### APISet Functionality

A `APISet` supports all classic set operations, such as union (`|`), intersection (`&`), difference (`-`), and symmetric difference (`^`). Additionally, it supports membership tests and other set-based operations. Functions called on the set are applied to every element, resulting in a new APISet with the processed data.

### The `filter()` Function

The `filter()` function uses a predicate to evaluate each element of the `APISet`. Elements where the predicate returns `true` are retained, while others are excluded, allowing precise control over the final set content.

### Flattening

When a function returns another `APISet`, the results are flattened into a single, unified `APISet`. This ensures a consistent set structure, simplifying further processing and analysis

### Functions that return APISet

* [`instruction.backward_df()`](../instruction/instruction.backward_df.md)
* [`instruction.forward_df()`](../instruction/instruction.forward_df.md)
* [`instruction.extended_next_instructions()`](../instruction/instruction.extended_next_instructions.md)
* [`instruction.extended_previous_instructions()`](../instruction/instruction.extended_previous_instructions.md)
* [`instruction.next_instructions()`](../instruction/instruction.next_instructions.md)
* [`instruction.previous_instruction()`](../instruction/instruction.previous_instruction.md)
* [`instruction.previous_instructions()`](../instruction/instruction.previous_instructions.md)
* [`callable.get_reachable_instructions()`](../callable/callable.get_reachable_instructions.md)



