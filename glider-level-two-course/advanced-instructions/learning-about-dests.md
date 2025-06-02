# Learning About Dests

## Querying for Assigned Variables

When writing a Glider Query, we will often have to query for variables. More importantly, we'll want to query for variables assigned in Solidity. For example, let's take the following Solidity code:

```solidity
function permit(address owner, address spender, uint value, uint deadline, uint8 v, bytes32 r, bytes32 s) external {
    // Code omitted for brevity
    
    address recoveredAddress = ecrecover(digest, v, r, s);
    require(recoveredAddress != address(0) && recoveredAddress == owner, 'Pancake: INVALID_SIGNATURE');
    _approve(owner, spender, value);
}
```

In this example, a variable named recoveredAddress is created and is used later on used to validate who wrote the signature. With Glider, we can identify the recoveredAddress variable and follow the variable usage. Below we will walk through this.

## What are Dests

When working with instructions, if an instruction creates or assigns a variable, Glider allows us to also query for the variables. Let's take the following Solidity example:

```solidity
uint256 length = locks.length;
```

In this example, the dest is considered the variable named length.

Let's look at another Solidity example:

```solidity
address owner;

function setNewOwner(address newOwner) {
    owner = newOwner;
}
```

In this example, owner is a state variable. Inside of the setNewOwner() function the owner state variable is updated with a new owner. Here, `owner = newOwner;` is the instruction we are looking at. The owner variable assigned here is the instruction's dest.

To summarize, the dest represents the left-most variable assigned in an instruction:

\[INSERT SCREENSHOT OF CODE WITH HIGHLIGHT ON WHAT THE DEST IS]

### How to retrieve variable instructions

If we want the query an instruction's dest, we can use the `get_dest()` function.

The `get_dest()` function is called against a single Instruction. To explain this further, let's take a look at the following Glider query:

```python
def query():
    instructions = Instructions().new_variable_instructions().exec(1, 10)
    
    instruction = instructions[0]
    
    return instructions
```

In this query, we identify the first new variable instruction and assign it to an instruction variable. This instruction variable is an Instruction object. With instruction objects, we can query for parts of the instruction. In our case, we want to query for the variables in the instruction.

To do this, we call `get_dest()` against the Instruction object. This is as simple as running

```python
instruction.get_dest()
```

By calling get\_dest(), Glider will return to us the variable assigned in the instruction.&#x20;

If the instruction doesn't assign any variables, then get\_dest() will return what's called a NoneObject.

{% hint style="info" %}
Glider will return NoneObjects when Glider is unable to find the queried object. A NoneObject in other words represents a situation where Glider attempted to query for something but couldn't find the value.
{% endhint %}

Let's now update our Glider query to identify the variable assigned in the instruction with `get_dest()`:

```python
def query():
    instructions = Instructions().new_variable_instructions().exec(1, 10)
    
    instruction = instructions[0]
    
    print(instruction.get_dest())
    
    return instructions    
```

Now we print out the variable assigned in the instruction. The Glider IDE debugger panel returns:

```python
<api.point.var_value.VarValue object at 0x75f3ed7fa9e0>
```

This represents the assigned variable. From here we can do much more with the assigned variable like see where the assigned variable flows into, what the variable is named, etc.



### Working with variable instructions

Once we've received the variable instruction, there is a lot we can do with the variable instruction





todos

* this section is incomplete. skipping for now because i need to think a bit about how i want to structure this section. ideally it should be
  * what is dest
  * why we need dest
  * querying for dest
  * examples





```

    - Dest represents the variables that are created/assigned in the instruction. They represent the destination of the return value of instructions. If an instruction calls a function and the return values are assigned to variables, the variables represent the dest.
        - note that get_dest() can return VarValues but also IndexAccess and others.
    - show example
        - Show glider example and code
    - common use cases
        - Used commonly to check if function return values are validated
            - transfer and transferFrom example
```
