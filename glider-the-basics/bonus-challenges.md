# Bonus Challenges

Now that we’ve covered the basics of Glider, it’s time to put your knowledge to the test with a series of bonus challenges. These challenges are designed to reinforce what you’ve learned by asking you to create queries that identify specific vulnerabilities, code patterns, or statistics.



## Challenge #1 - Calls to Curve's get\_virtual\_price()

Curve pools have a **get\_virtual\_price()** function that returns the price of the Curve pool’s LP token. However, due to a [known reentrancy vulnerability](https://www.chainsecurity.com/blog/curve-lp-oracle-manipulation-post-mortem) in Curve pools, the **get\_virtual\_price()** function can be manipulated by attackers.

If a third-party contract relies on **get\_virtual\_price()** to determine the LP token price, that contract can also be vulnerable to exploitation.

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/Eb7Q9mBk](https://glide.r.xyz/query/Eb7Q9mBk)

</details>



## Challenge #2 - Find Long Function Names

In this challenge, your task is to identify functions that have more than 55 characters in it's function name.&#x20;

{% hint style="info" %}
We can use Python's len() function to check how many characters a Solidity function has.
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/BK94oa8HZ](https://glide.r.xyz/query/BK94oa8HZ)

</details>



## Challenge #3 - Arbitrary Spender Roles

Contracts that approve tokens to other addresses must ensure that the spender address is properly whitelisted. Failing to do so can lead to serious security risks. For example, in December 2024, [Moonhacker experienced an attack](https://blog.solidityscan.com/moonhacker-vault-hack-analysis-ab122cb226f6) where hackers were able to arbitrarily set the spender address for the approve() function, leading to significant losses.

In the next two challenges, we will aim to write a query to identify this vulnerability type.



### Challenge #3a - Get ERC20.approve() Spender

In this challenge, your goal is to:

1\. Find calls to the ERC20 **approve()** function.

2\. Identify the spender argument passed to the **approve()** function.

3\. Print the spender argument to the Glider IDE Output panel to confirm your results.

{% hint style="info" %}
This challenge will require you to use function/methods that you haven’t worked with before. Since the goal is to identify calls and print out call arguments, the following Glider methods will be helpful:

* [get\_components()](https://glide.gitbook.io/main/glider-ide/api/instruction/instruction.get_components) – To retrieve the different parts of an instruction.
* [get\_arg()](https://glide.gitbook.io/main/glider-ide/api/value/call/call.get_arg) – To find the spender argument in a call.
* [isinstance()](https://www.w3schools.com/python/ref_func_isinstance.asp) - Checks if a variable belongs to a specific class.
{% endhint %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/Sx82Nnjq](https://glide.r.xyz/query/Sx82Nnjq)

</details>



### Challenge #3b - Find Arbitrary Spenders

In the second part of this challenge, your goal is to determine if the spender argument passed to the **approve()** function comes from a function argument. If the spender originates from a function argument, it likely means that the user can arbitrarily set the spender, which could be a potential security risk.

{% hint style="info" %}
To check if a variable comes from a function argument, call [get\_object\_of\_var()](https://glide.gitbook.io/main/glider-ide/api/point/varvalue/varvalue.get_object_of_var) on the variable and verify if it is an instance of [ArgumentVariable](https://glide.gitbook.io/main/glider-ide/api/variables/argumentvariable).
{% endhint %}

#### **Bonus Task**

To reduce noise and focus just on public/external functions, update your query to filter out approve() calls made within private or internal functions.

By limiting your results to public or external functions, you can better identify potential vulnerabilities that external users could exploit.

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f4a1">💡</span> Click here for the solution</summary>

Stuck or want to confirm your answer? Visit the link below where you can view and run the solution inside of Glider IDE:

[https://glide.r.xyz/query/BRsBRayJq](https://glide.r.xyz/query/BRsBRayJq)

</details>
