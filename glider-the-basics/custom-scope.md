# Custom scope

### What is Custom Scope? <a href="#what-is-custom-scope" id="what-is-custom-scope"></a>

Custom scopes let you run queries against your own set of deployed Solidity contracts instead of an entire chain. This makes queries run faster and gives you precise control over what contracts you work with.

### Why it matters <a href="#why-it-matters" id="why-it-matters"></a>

1. **Iterate faster**\
   Executing against a full chain can take from a couple of seconds to minutes. With a custom scope, it only takes seconds because you’re querying just a handful of contracts.
2. **Signal over noise**\
   Focus on the exact contracts you care about while you iterate on detections.
3. **Tighter feedback loop**\
   Quickly harden queries before you scale them to chain-wide runs.

### Use case: Rapid incident response <a href="#use-case-rapid-incident-response" id="use-case-rapid-incident-response"></a>

Scenario: a new vulnerability is exploited and you want to ship a Glider query to find other occurrences on-chain.

1. **Collect addresses**\
   Gather the deployed addresses of the vulnerable contracts (from the incident write-up, explorer).
2. **Create a custom scope**\
   Put those addresses in a new scope and compile.
3. **Develop your query**\
   Iterate on the query against the custom scope until it reliably flags the vulnerable contracts.
4. **Scale up safely**\
   Once your query is stable, switch execution to the relevant chain and run it broadly to find additional affected contracts or patterns.

Repeat as needed: refine the query in the scope, then re-run on chain to widen coverage.

### Use case: Hitting memory or output limit <a href="#use-case-hitting-memory-or-output-limit" id="use-case-hitting-memory-or-output-limit"></a>

If your query hits a memory or output limit, you likely need to narrow it down. Check Performance → Profiler, or compile a custom scope and iterate your query against a handful of contracts.

### Create a custom scope <a href="#create-a-custom-scope" id="create-a-custom-scope"></a>

1. Open [My Scopes](https://glide.r.xyz/my-scopes/) → click [Create new scope](https://glide.r.xyz/my-scopes/create).
2. Add contracts\
   Add up to 5 addresses from verified contracts on 30+ supported chains.
3. Compile\
   Compilation takes up to a minute
4. Query your scope\
   Once compiled, click Open in IDE to start querying the scope

### Limitations <a href="#limitations" id="limitations"></a>

1. Users are limited to a single custom scope. You can edit your scope unlimited number of times.
2. Users are limited to deployed contracts only. You may want to deploy your contract on Sepolia if it's not on chain yet.
3. Users are limited to 5 contracts.
4. Users can only add verified contracts. Meaning that if the contract owner didn't verify the source code, it won't be visible.
5. Only scopes with the Compiled successfully status appear in the Execution Scope selector. Pick the scope, then run your queries
