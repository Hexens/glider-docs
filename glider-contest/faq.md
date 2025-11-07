---
description: Find frequently asked questions about Glider and the Glider contest below.
icon: question
cover: ../.gitbook/assets/Glider QDB (1).png
coverY: 0
layout:
  width: default
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# FAQ

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="2b50">⭐</span> How do I start writing Glider queries?</summary>

* Start with the [Glider Basics](https://glide.gitbook.io/main/glider-ide/glider-the-basics)
* Join [Remedy Discord Server](https://discord.com/invite/remedy) for educational content and support from the Community.

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="2b50">⭐</span> Can I use AI to navigate through Glider Documentation faster?</summary>

Yes. If you’re using an external AI assistant (like ChatGPT, Claude, or a local LLM), you can feed it the full Glider API documentation to improve context and accuracy.\
To generate a single file containing all API docs from our GitHub repo, run this one-line command in your terminal:

```
git clone
 https://github.com/Hexens/glider-docs
 tmp-repo 2>/dev/null || (cd tmp-repo && git pull) && find tmp-repo/api -name "*.md" -type f -print0 | xargs -0 cat > api-docs-merged.md && rm -Rf tmp-repo
```

</details>

<details>

<summary>Is there any Remedy fee if I find a bounty-eligible bug with Glider?</summary>

No. Remedy doesn’t claim any rewards, fees, or commissions associated with any bug bounties researchers are able to claim.

</details>

<details>

<summary>What is “Rarity”?</summary>

Rarity (Uncommon/Rare/Epic/Legendary) is used to measure Glider query’s quality. It is set by the triager using weighted risk metrics (e.g., Risk Likelihood, Impact, Potential, Initial Damage, Remedy Opinion). Legendary is the rarest.

Learn more about rarity and how it's being defined in [triage-guidelines.md](triage-guidelines.md "mention")

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="2b50">⭐</span> Which bugs are queryable with Glider?</summary>

Ideally participants should come up with any vulnerability scenario that no one has reported yet, if you run out of ideas you can always check out [recommended-vulnerabilities-to-query.md](recommended-vulnerabilities-to-query.md "mention") for hand-picked bugs that are suggested to formalize as Glider queries.

</details>

<details>

<summary>What is Glider Watcher?</summary>

Glider Watcher lets you schedule recurring query runs and notifies you only when new results appear on-chain. This feature is available exclusively for Legendary Queries.

</details>

<details>

<summary>Can I ask to keep my query’s code private and get contest monetary rewards?</summary>

No, however, in certain cases, the Triager has the right and the ability to set the visibility to hidden after the reward was paid out to the author, to provide ample time for the protocol to be fixed. If the query was hidden by Triager for responsible disclosure to the protocol, after the implementation of the fix or expiration of 60 calendar days after the finding, the query will again become visible.

</details>

<details>

<summary>Who and how assess the queries?</summary>

After query submission, the system creates a thread with a Remedy triager. All communications around the submission take place in that thread.&#x20;

Learn more about the [triage-guidelines.md](triage-guidelines.md "mention")

</details>

<details>

<summary>What are “optimizations” and why do they matter?</summary>

Optimizations are improvements to an existing Glider query. They aim to: result in a safer, fresher query that finds more real issues with less noise.

</details>

<details>

<summary>How do optimizations work? What happens to the original query?</summary>

When your optimization is approved, it becomes the active version. The previous one is marked Outdated. The Query DB shows origin and last iteration for credit.

</details>

<details>

<summary>What are Glider limitations?</summary>

Output memory: 200 KB. Execution timeout: 1000 seconds. See more limits in the Glider [docs](https://glide.gitbook.io/main/glider-ide/limitations#output-limit).

</details>

<details>

<summary>Can I run my query on chains other than Ethereum mainnet?</summary>

Not yet. On-chain runs are limited to Ethereum mainnet. After approval, we provide a one-time cross-chain results snapshot for supported chains. We’ll add more chains in phases. If you need a specific chain, mention it in your submission thread.

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="2b50">⭐</span> Where can I ask questions?</summary>

oin [Discord](https://discord.com/invite/remedy) to get help from the community and Glider experts.

</details>

<details>

<summary>How to get paid for Glider Contest participation?</summary>

Write a Glider query that detects a smart contract vulnerability on any EVM chain. Queries targeting past exploits and known vulnerabilities are eligible for rewards.\
If your query uncovers a real-world issue with funds at risk, your Query Rarity and contest payout may increase!

</details>
