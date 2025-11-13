---
icon: clipboard-list-check
---

# Glider Cheatsheet

This cheatsheet brings together a collection of Glider query code snippets, designed to help you write queries more effectively without starting from scratch.

### Identify the function from an instruction&#x20;

#### Problem:

I want to find the function an Instruction belongs to.

#### Solution:

```python
def query():
    # If you have an instruction and want to find a function
    instruction = Instructions().exec(1)
    function = instruction.get_parent()

    return function
```

### Check if a variable comes from a function argument&#x20;

#### Problem

Given a VarValue, I want to see if the VarValue comes from a function argument.

> This type of query is helpful when you want to see if a variable comes from user-input.

#### Solution

```python
def query():
    # The find_var_value() function is used for demo purposes. VarValues are the only components in Glider that can be sourced from a function argument.
    var_value = find_var_value()
 
    # Here we check if a VarValue comes from a function argument. 
    is_function_argument = isinstance(var_value.get_object_of_var(), ArgumentVariable)

    # If true, the VarValue comes from a function argument. If false, the VarValue doesn't come from a function argument.
    print(is_function_argument)
 
     # For now we don't return any results, but based on the is_function_argument variable above you can choose to keep or remove results.
    return []


# Function is used for demo purposes.
def get_components_recursive(component):
    components = []

    try:
        # Since we are dealing with a call, we get the call arguments as components
        if isinstance(component, Call):
            components = component.get_args()
        else:
            # Get components within components
            components = component.get_components()
    except Exception:
        # This handles cases where the component can't be broken down further
        None

    results = []

    for comp in components:
        results.append(comp)
        for sub in get_components_recursive(comp):
            results.append(sub)
    
    return results


# This function is used for demo purposes only.
def find_var_value():
    # Get some instructions for demo purposes
    instructions = Instructions().exec(10)
 
    # Get components for demo purposes
    components = get_components_recursive(instructions[1])

    var_values = []

    # Iterate through components for demo purposes
    for component in components:
        # Collect VarValues from the components for demo purposes
        if isinstance(component, VarValue):
            var_values.append(component)


    # In Glider, the VarValue represents a value that could come from a function argument.
    if len(var_values):
        return var_values[0]

    return []
```

### Check if require or assert statement is called inside a function

#### Problem #1

I need to know if a require or assert statement is made inside a function.

#### Solution #1

```python
def query():
    # The function variable represents a function we are querying
    functions = Functions().exec(100)

    # We can pass has_guard_check into a filter to filter out results.
    functions_with_guard_checks = functions.filter(
        lambda function : 
        any(function.instructions().with_one_of_callee_names(["require", "assert"]).exec())
    )

    return functions_with_guard_checks
```

#### Problem #2

I want to know if the Instruction I'm working with is a require or assert statement.

#### Solution #2

```python
def query():
    # Find some instructions for demo purposes
    instructions = Instructions().exec(1,1)

    # We can pass has_guard_check into a filter to filter out results.
    print(has_guard_check(instructions[0]))

    return instructions
 
 
# The has_guard_check function can be used to filter out if a function has a require/assert statement.
def has_guard_check(instruction):
    # This will retrieve all of the calls made in the instruction
    callee_names = instruction.callee_names()
    # Checks if require or assert are called in the Instruction.
    return "require" in callee_names or "assert" in callee_names
```

### Check if a function is called in another function

#### Problem

I need to find the functions that call a particular function, where the only information I have is the name of the function being called.

#### Solution

```python
def query():
    # If we want to find functions that call deposit(), we first set the function_name to deposit.
    function_name = "deposit"

    # Now we search for deposit functions.
    functions = Functions().with_name(function_name).exec(5)

    # By calling caller_functions(), we can find all of the functions that call deposit()
    functions_that_call_deposit = functions.caller_functions().exec()

    return functions_that_call_deposit
```

### Filter out interface functions

#### Problem

I want to remove interface functions from my results.&#x20;

#### Solution

```python
def query():
    # Find some functions for demo purposes
    functions = Functions().exec(10)

    # Identify impl functions via filtering with the is_implementation_function function
    implementation_functions = functions.filter(is_implementation_function)

    return implementation_functions


# This function checks if a function is implemented and not just a function defined in an interface.
def is_implementation_function(function):
    # We can determine if a function is implemented or not by if it has instructions. If a function has instructions, we know it has code.
    return any(function.instructions().exec())
```

### Get all variables used in an instruction

#### Problem

I want to find all of the variables and components in a given Instruction.

#### Solution

```python
def query():
    # Find some instructions for demo purposes
    instructions = Instructions().exec(100)
 
    # Iterate through instructions for demo purposes
    for inst in instructions:
        # To get all of the components inside an Instruction, we can use the get_components_recursive function to get all components inside an Instruction
        components = get_components_recursive(inst)   
        
        # Now we can work with the components variable like iterating, filtering, etc.    
 
    return []


# This function accepts a component as an argument whether that's an Instruction or another component. The function returns an array of sub-components.
def get_components_recursive(component):
    components = []

    try:
        # Get components of an IndexAccess
        if "IndexAccess" in str(component): 
            components.append(component.get_sequence()) 
            components.append(component.get_index())

        # If we are dealing with a call, we get the call arguments as components
        if isinstance(component, Call):
            components.extend(component.get_args()) 
            call_qualifier = component.get_call_qualifier()

            # Get components of an IndexAccess
            if "IndexAccess" in str(call_qualifier): 
                components.append(call_qualifier)
                components.append(call_qualifier.get_sequence()) 
                components.append(call_qualifier.get_index())
        else:
            # Get components within components
            components = component.get_components()
    except Exception:
        # This handles cases where the component can't be broken down further
        None

    results = []

    for comp in components:
        results.append(comp)
        results.extend(get_components_recursive(comp))
    
    return results
```

### Identify state variables in a contract

#### Problem

I want to find every state variable for a contract.

#### Solution

```python
def query():
    # Find contracts for demo purposes
    contracts = Contracts().with_name("UniswapV3Pool").exec(1)

    contract = contracts[0]

    # To get state variables of a contract, we can call state_variables().exec() against a contract
    state_variables = contract.state_variables().exec()

    # Print the state variable names for convenience
    print(state_variables.name)

    return state_variables
```

### Identify instructions doing arithmetic

#### Problem

I want to know if a given Instruction contains math arthimetic.

#### Solution

```python
def query():
    return Instructions().exec(1000).filter(does_arithmetic)


# This function checks if a given instruction does arithmetic.
def does_arithmetic(instruction):
    solidity_arithmetic = ["-", "+", "/", "*", "**", "%", "++", "--", "+=", "-=", "*=", "/=", "%="]
    components = get_components_recursive(instruction)
    
    for component in components:
        if "Operator" in str(component):
            if component.expression in solidity_arithmetic:
                return True
            
    return False
    
    
# This function accepts a component as an argument whether that's an Instruction or another component. The function returns an array of sub-components.
def get_components_recursive(component):
    components = []

    try:
        # Get components of an IndexAccess
        if "IndexAccess" in str(component): 
            components.append(component.get_sequence()) 
            components.append(component.get_index())

        # If we are dealing with a call, we get the call arguments as components
        if isinstance(component, Call):
            components.extend(component.get_args()) 
            call_qualifier = component.get_call_qualifier()

            # Get components of an IndexAccess
            if "IndexAccess" in str(call_qualifier): 
                components.append(call_qualifier)
                components.append(call_qualifier.get_sequence()) 
                components.append(call_qualifier.get_index())
        else:
            # Get components within components
            components = component.get_components()
    except Exception:
        # This handles cases where the component can't be broken down further
        None

    results = []

    for comp in components:
        results.append(comp)
        results.extend(get_components_recursive(comp))
    
    return results  
```

### Identify functions that receives or send ETH

#### Problem

I want to know if a function receives or sends ETH.

#### Solution

```python
def query():
    return Functions().exec(10000).filter(calls_other_contract).filter(can_receive_eth)
    
    
# This function is used to identify if a function makes a low-level external call to another contract.
def calls_other_contract(function):
    transfers_eth = function.instructions().low_level_external_calls().exec().filter(sends_eth_in_transfer)

    return any(transfers_eth)


# This function checks if a low-level external call instruction sends ETH to another EOA/contract
def sends_eth_in_transfer(instruction):
    if instruction.get_value():
        for call in instruction.get_value().get_callee_values():
            if call.name == "call" and len(call.get_call_value()) > 0:
                return True

    return False


# This function checks if a function is payable and can receive ETH
def can_receive_eth(function):
    return function.is_payable()  
```

### Find functions without a modifier

#### Problem

I want to find functions that don't call onlyOwner.

#### Solution

```python
def query():
    return (
        Functions()
        .without_modifier_name("onlyOwner")
        .exec(10)
    )
```

### Check if a function has a given argument by type

#### Problem

I want to determine if a function has an argument type like address, uint256, etc.

#### Solution

```python
def query():
    return (
        Functions()
        .exec(10)
        .filter(has_address_argument)
    )

# Returns true when the function has an address argument
def has_address_argument(function):
    return "address" in function.arguments().list().get_variable().type.name
```

### Check for msg.sender validations

#### Problem

I want to check if a function has any msg.sender validations.

#### Solution

```python
from glider import *

def query(): 
    return (
        Functions()
        .exec(1000) 
        .filter(validates_msg_sender)
    )
 
# Note: msg.sender passed into a Call or used as IndexAccess and the return value is equated against are treated as a msg.sender validation.
def validates_msg_sender(function):
    for instruction in function.instructions_recursive():
        if revert_condition(instruction) and potential_msg_sender_call(instruction):
            return True 

    return False 
    

# Checks if revert is called
def revert_condition(instruction):
    builtin_callee_names = instruction.callee_names()
    if 'require' in builtin_callee_names or 'assert' in builtin_callee_names:
        return True

    if not instruction.is_if():
        return False
        
    return any('revert' in x for x in instruction.first_true_instruction().callee_names())


# Checks if an instruction calls msg.sender in any call
def potential_msg_sender_call(instruction):
    components = get_components_recursive(instruction)

    for component in components:
        # Ignore Calls and IndexAccesses since they produce a large number of FPs.
        if isinstance(component, Call) or "IndexAccess" in str(component):
            continue

        # There are cases where msg.sender is passed into a check that isn't validating the msg.sender address. For example balance >= balances[msg.sender]. This skips those cases.
        if isinstance(component, ValueExpression) and not contains_equality_op(component):
            continue

        for msg_sender_call in msg_sender_calls():
            if msg_sender_call in component.source_code(): 
                return True

    return False


# Iterate through a component's operations and check for equality checks. 
def contains_equality_op(component):
    ops = component.get_components().filter(lambda component : "Operator" in str(component)).get_operator()

    for operator in ops:
        if "OperatorType.NOT_EQUAL" in str(operator) or "OperatorType.EQUAL" in str(operator):
            return True

    return False

# Returns a list of common ways to retrieve msg.sender
def msg_sender_calls():
    return [
        "msg.sender",
        "msgSender",
        "_msgSender",
        "_msgSenderERC1155",
        "caller" # Assembly msg.sender call
    ]


# Returns all components in Instruction through recursive manner suited for msg.sender validations.
def get_components_recursive(component):
    components = []
    results = [] 

    try:
        # If we are dealing with a call, we get the call arguments as components
        if isinstance(component, Call):
            components.extend(component.get_args()) 
        else:
            # Get components within components
            components = component.get_components()
    except: 
        # This handles cases where the component can't be broken down further
        None

    for comp in components:    
        results.append(comp)

        for sub_comp in get_components_recursive(comp):
            results.append(sub_comp)

    return results
```

####

### Check if an instruction could revert

#### Problem

I want to check if an instruction could revert either through a require or assert check or a direct call to a revert.

#### Solution

```python
def revert_condition(instruction):
    builtin_callee_names = instruction.callee_names()
    if 'require' in builtin_callee_names or 'assert' in builtin_callee_names:
        return True

    if not instruction.is_if():
        return False
        
    return any('revert' in x for x in instruction.first_true_instruction().callee_names())
```
