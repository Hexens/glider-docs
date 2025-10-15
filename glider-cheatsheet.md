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
        any(function.instructions().exec().filter(has_guard_check))
    )

    return functions_with_guard_checks
 
 
# The has_guard_check function can be used to filter out if a function has a require/assert statement.
def has_guard_check(instruction):
    # This will retrieve all of the calls made in the instruction
    callee_names = instruction.callee_names()
    # Checks if require or assert are called in the Instruction.
    return "require" in callee_names or "assert" in callee_names
```

#### Problem #2

I want to know if the Instruction I'm working with is a require or assert statement.

#### Solution #2

```python
def query():
    # The function variable represents a function we are querying
    function = Functions().exec(1)[0]

    # Find some instructions for demo purposes
    instructions = function.instructions().exec()

    # We can pass has_guard_check into a filter to filter out results.
    instructions_with_guard_checks = instructions.filter(has_guard_check)

    return instructions_with_guard_checks
 
 
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
            components = component.get_args()
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
        for sub_comp in get_components_recursive(comp):
            results.append(sub_comp)
    
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
    
    
# This function finds all components within a given instruction and/or component.    
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
        for sub_comp in get_components_recursive(comp):
            results.append(sub_comp)
    
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

I want to check if a function does any msg.sender validations.

#### Solution

```python
def query():
    return (
        Functions()
        .exec(100)
        .filter(missing_msg_sender_validations)
    ) 
 

# Checks if a given function is missing msg.sender validations
def missing_msg_sender_validations(func):
    # instructions() is temporary and in reality we should use instructions_recursive().
    instructions = func.instructions().with_one_of_callee_names(["require", "assert"]).exec()
    if not any(instructions):
        return True

    for inst in instructions:
        if calls_msg_sender(get_components_recursive(inst)):
            return False 

    return True
 

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
            components = component.get_args()
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
        for sub_comp in get_components_recursive(comp):
            results.append(sub_comp)
    
    return results


# Checks if a given list of components contains a call to msg.sender
def calls_msg_sender(values):
    # Common msg sender functions
    msg_sender_calls = [
        "msg.sender",
        "msgSender",
        "_msgSender",
        "msgSender()",
        "_msgSender()"
    ]

    # Checks if any of the components contain a call to msg.sender.
    return any(value.expression in msg_sender_calls for value in values) 
```
