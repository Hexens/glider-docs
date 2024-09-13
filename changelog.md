---
description: Page to follow the updates on Glider engine
---

# Changelog

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

####
