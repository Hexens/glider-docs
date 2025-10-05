---
description: >-
  Returns a list of all instructions following the current point in the current
  data flow graph
---

# Value.forward\_df()

`forward_df() -> APISet[Point]`

The function works similarly to [Instruction.forward\_df()](../../instruction/instruction.forward_df.md); the main difference is that in case of Instruction.forward\_df() the function will return forward-dataflow point for every point in the instruction, while Value.forward\_df() returns only those connected with the current Value.&#x20;

## Query Example

Consider the following Solidity function:

```solidity
function registerDatasetProfile(string memory contributor,string memory coverage,string memory creator,string memory date,string memory description,string memory format,string memory identifier,string memory language,string memory publisher,string memory relation,string memory rights,string memory source,string memory subject,string memory title,string memory dtype)
    public returns (uint)
    {
        lastDatasetId = lastDatasetId + 1;
        datasetOwners[lastDatasetId] = msg.sender;
        emit AssignDatasetId(lastDatasetId,msg.sender);
        metadata[lastDatasetId]['contributor'] = contributor;
        metadata[lastDatasetId]['coverage'] = coverage;
         metadata[lastDatasetId]['creator'] = creator;
         metadata[lastDatasetId]['date'] = date;
         metadata[lastDatasetId]['description'] = description;
         metadata[lastDatasetId]['format'] = format;
         metadata[lastDatasetId]['identifier'] = identifier;
         metadata[lastDatasetId]['language'] = language;
         metadata[lastDatasetId]['publisher'] = publisher;
         metadata[lastDatasetId]['relation'] = relation;
         metadata[lastDatasetId]['rights'] = rights;
         metadata[lastDatasetId]['source'] = source;
         metadata[lastDatasetId]['subject'] = subject;
         metadata[lastDatasetId]['title'] = title;
         metadata[lastDatasetId]['type'] = dtype;
         
         return lastDatasetId;
    }
```

In this Solidity example, we want to identify where the lastDatasetId variable flows to.&#x20;

To do this, we first query for the instruction that assigns the lastDatasetId variable:

```solidity
lastDatasetId = lastDatasetId + 1;
```

We then select the lastDatasetId component, and call forward\_df() to identify every point the lastDatasetId flows to.

<pre class="language-python"><code class="lang-python"><strong>from glider import *
</strong>
def query():
    instructions = (
        Functions()
        .with_name("registerDatasetProfile")
        .exec(1)
        .instructions()
        .exec(2)
    )

    for instruction in instructions:
        components = instruction.get_components()
        for component in components:
            print("Value: " + component.expression)

            for point in component.forward_df():
                print("Flows to: " + point.source_code())

            break

    return instructions
</code></pre>

## Example Output

<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-04 at 12.24.59 PM.png" alt=""><figcaption></figcaption></figure>
