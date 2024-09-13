---
description: Page to follow the updates on Glider engine
icon: list-check
---

# Changelog

## V1.0(28.08.2024):

### API

Added functions:&#x20;

* Add `filter` function in `APIIterable`

Refactoring:&#x20;

* Make some functions deprecated:
  * `Functions::with_all_properties`
  * `Functions::with_one_property`
  * `Functions::without_properties`

Bug fixes:

* Add `source_code` for all entities



## V0.9(23.08.2024):

### API

Added functions:&#x20;

* Added `Modifier::properties()`
* Added `StateVariable::is_accessible`

Refactoring:&#x20;

* Changed return types of some functions from `APIList` to `APISet`
  * `next_instructions`
  * `previous_instruction`
  * `previous_instructions`
  * `forward_df`
  * `backward_df`
  * `extended_forward_df`
  * `extended_backward_df`
* Update `APIIterable` implementation:
  * Now any function, that retunrs any `APIIterable`, that called on `APIIterable` be flattened
  * Exlude `NoneObjects` form the `APIIterable`

Bug fixes:

* `extended_backward_df`/`has_extended_global_df` does not return `state_vars` (when the state var is declared in base contracts) Now `extended_backward_df`/`has_extended_global_df` will work for inherited private variables too.
* Fixed TypeError: `NoneObject` object is not iterable

## V0.8(01.08.2024):

### API

Added functions:&#x20;

* Added `Point::has_extended_global_df`

Refactoring:&#x20;

* Added types for `Values`

Bug fixes:

* Take into account the functions called when calling `Instruction::extended_backward_df`.
* Take into account the functions called when calling `Instruction::extended_backward_df`.
* Fixed `extended_forward_df`. It couldn’t go through the multiple chain of calls

Optimizations:

* Optimized (about 10%) `extended_next_instructions` function

## V0.7(09.07.2024):

### API

Added functions:&#x20;

* Added `Functions::with_properties_considering_modifiers`
* Added `ArgumentPoint` class
* Added `StatePoint` class
* Added `GlobalPoint` classes
* Added custom iterables. Now there are, `APIList`, `APISet` and `APITuple`.

Refactoring:&#x20;

* Rename class `Var` to `VarValue`
* Rename a function `Vars::get_definig_nodes` -> `Vars::get_definig_points`. Also, the return type has changed. Now it is possible to use it as an API function.
* Changed the return type of `Contract::errors()` from `List["api.Error"]` to `"api.Errors"`

Bug fixes:

* Take into account called functions when calling `Instruction::extended_previous_instructions`. The algorithm includes the instructions of called functions too.

## V0.6(21.06.2024):

### API

Added functions:&#x20;

* Added `AssemblyInstruction::get_block_instructions`
* Added global taint sources - `MSG_SENDER`, `MSG_VALUE`, `BLOCK_TIMESTAMP`, `NOW`, `TX_ORIGIN`
* Added API functions to filter `functions`/`modifiers` with custom property expression
  * `Functions::with_properties()`
  * `Functions::with_modifier_properties()`
  * `Modifiers::with_properties()`
  * Added `HAS_GLOBAL_VARIABLES_READ`for `functions`/`modifiers` propetry expression
  * Example: `Functions::with_modifier_properties(HAS_ARGS & (~HAS_CALLEES | IS_PRIVATE))`
* Added `Callable::new_contract_instructions` and `Instructions::new_contract_instructions` functions to get `instructions` that create a new contract. Also added `Instruction::is_new_contract` function
* Added `Callables::extended_callee_functions`
* Added `Functions::extended_caller_functions`
* Added `Functions::extended_caller_modifiers`

Refactoring

* Removed `Instrucitons::asm_instructions()`
* Made Instruction's operands single `Value`
* `Function::return_tuple` returns `Value`

Bug fixes:

* Added missing return data types
* Fixed bug in the data flow graph

## V0.5 (16.05.2024):

### API

Added functions:

* Callable.extended\_callee\_functions()
* Callable.extended\_instructions()
* Function.extended\_caller\_functions()
* Functions.with\_declarer\_contract\_name()
* Value.get\_state\_vars()
* Value.get\_local\_vars()
* Value.get\_global\_vars()
* Value.get\_arg\_vars()
* Value.get\_vars()

Refactorings:

* Introduced a common base class Variable
* function name refactorings
* entity names and type and similar fields became properties (methods before)
* ConditionalExpression is removed, and the ValueExpression-s will express that instead.

Bug fixes:

* modifier property filter bug fix
* different fixes with Value/Call functionality
* fixes in extended\* functions

Optimizations:

* Implemented query caching; this works only for the DB query part. Whenever a user runs a query, the DB query (declarative) part will get cached for some time, and the next run will return the DB output instantly. This hugely improves the process of writing queries as usually the most debugging is done after the DB results are fetched, e.g. on dataflow checks. The cache is global, so in case one user has already queried the exact same thing, other users will not wait for the result as well
* Query translation optimizations
* Query execution optimization.

