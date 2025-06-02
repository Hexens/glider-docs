# Understanding Types of Values

## Types of Values

When we receive a Value from a Glider query, we will receive a specific type of Value. Different value types represent different types of Solidity code.

This section will go over specific types of values, how to use them in your queries, and common examples you'll come across.

Before we get started, let's take a look at the following Glider query, which we will re-use throughout this section to&#x20;

##

* Understanding Value Types
  * with instructions (most common use case)
    * instruction dests
      * VarValue (TODO: can this be another value besides VarValue? Yes)
    * Calls
      * What are they
      * What can you get from them?
        * Call source code
          * source\_code()
          * Returns the source code of the call including the method name and args passed to the function. Returns a string.
        * Call name
          * name
          * Returns the function name called. Returns a string.
        * Call args
          * get\_args()
          * Represents the arguments passed to the function. Returns one or more Values.
          * We can
        * Call qualifier
          * purpose
          * show example
    * Instruction variables (VarValues)
      * get vars via instruction.get\_components().get\_vars()
