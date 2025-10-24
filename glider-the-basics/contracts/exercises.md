# Exercises

## Intro

In this section, we will present several exercises that will fortify your Functions query skills. Each exercise provided comes along with a solution if you get stuck.



## **Exercise #1 - Contracts Containing the Term "Swap"**

In this exercise, your task is to identify contracts that contain the term "Swap" in their contract names.

As we’ve done in previous sections, start by reviewing the [Glider API documentation](https://glide.gitbook.io/main/glider-ide/api) to find any Glider functions that can help you find contracts by their name.

**Challenge**: Find the necessary Glider function that finds contracts given a regex. Then update the query with the found Glider function.

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/dqRy2mMQ](https://glide.r.xyz/query/dqRy2mMQ)

</details>



## **Exercise #2 - Finding Contracts with the "setOracleAddress" Function**

Now that we’ve identified contracts with names containing the word "Swap", let’s take it a step further by filtering for contracts that contain the **setOracleAddress** function.

**Challenge**: Update your query from Example #1 to filter out contracts that don’t contain the **setOracleAddress** function.

{% hint style="info" %}
Refer to the [Contracts API documentation section](https://glide.gitbook.io/main/glider-ide/api/contracts) to find the function needed to complete this challenge.
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/aDh9w1dg](https://glide.r.xyz/query/aDh9w1dg)

</details>



## **Exercise #3 - Finding the Main Contract**

A Solidity contract may inherit from parent contracts. Both the main contract and its parent contracts share the same address. When querying contracts, Glider may return multiple associated contracts in the results.

To specifically identify the main contract, you can use Glider’s `mains()` method.

**Challenge**: Update the query to return only the main contracts from the query results.

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/XO5B77O0](https://glide.r.xyz/query/XO5B77O0)

</details>



## **Exercise #4 - Functions Without Modifiers**

This query has focused on identifying swap-like contracts that update their oracle address through a Solidity function called **setOracleAddress**. But what if we want to return all functions that don’t have modifiers?

Identifying functions without modifiers can help us uncover potential access control vulnerabilities, as these functions may be publicly accessible without restrictions.

Thankfully, we can achieve this with Glider!

To do so, we’ll:

1\. Iterate through each contract function.

2\. Count the number of modifiers applied to each function.

3\. Filter out functions with modifiers to focus only on unrestricted functions.

This approach will give us a list of functions without modifiers, helping us identify any security risks in the contract.

**Challenge**: Update the query from Exercise #4 to return functions without modifiers.

{% hint style="info" %}
Using a `filter()` can simplify our query.
{% endhint %}

{% hint style="info" %}
In this query, we’ll need to retrieve each contract’s functions. As a hint, refer to the relevant [Glider method](https://glide.gitbook.io/main/glider-ide/api/contracts/contracts.functions) in the documentation that allows you to query a contract’s functions.
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/BO6sjUbvb](https://glide.r.xyz/query/BO6sjUbvb)

</details>



## Bonus Challenge

We want to look for state variables in a contract.&#x20;

**Challenge**: Identify the Glider class that will query for state variables.

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/2tGaiLV](https://glide.r.xyz/query/2tGaiLV)

</details>
