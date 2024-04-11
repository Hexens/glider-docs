---
description: Basic concepts of using API module
---

# 📌 Main concepts

The part of a glider code that will query information from DB is contained in the API module, as well as other high-level graph functions can be found there.

The query chain is constructed in DSL format

```python
instructions = (
    Functions()
    .with_one_property([MethodProp.EXTERNAL, MethodProp.PUBLIC])
    .without_properties([MethodProp.HAS_MODIFIERS, MethodProp.IS_CONSTRUCTOR])
    .instructions()
    .with_called_function_name("selfdestruct")
    .exec()
)
```

As you can see here, the chain consists of different types of filterings, such as with\_one\_property, without\_properties, etc.

The way to think of this filter chain is that every filter narrows down the set of results before entering the next filter chain. In other words, the filters can also be thought of as a chain joined with a logical AND operator.

## Changing entities

As can be seen from the code above, the chain can also change the entity it is filtering on.

Here, the part `.instructions()` will "level down" to the instructions of the functions that have been filtered previously in the chain, and the user can continue filtering on the new type of entity.&#x20;

Likewise, a "level-up" can also be made, for example, starting filtering with instructions and then changing the query entity to functions.

## Performance note

One should consider performance issues coming from changing entities multiple times during a chain of queries.

In such situations, it is much more effective to break it into multiple query chains and then combine the results.

## Pagination of results

The last part of the query always ends with .exec() call, which can also be used to paginate the results in case the returned set is big.

The function can be called with parameters:

`exec(limit)`

`exec(offset,limit)`
