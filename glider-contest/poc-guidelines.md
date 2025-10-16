---
icon: stamp
cover: ../.gitbook/assets/Glider QDB.png
coverY: 0
---

# PoC Guidelines

### Overview <a href="#overview" id="overview"></a>

A Proof of Concept (PoC) in the Glider Query Contest is a practical demonstration showing that a vulnerability detected by a query is real and can be reproduced against a returned Glider result.\
It should clearly prove that the issue exists under real on-chain conditions, while remaining safe for both users and networks.\
All tests must stay local and isolated from live systems such as the Ethereum mainnet or public testnets.

A well-written PoC is easy to understand, simple to run, and transparent about what it verifies.

***

### Environment <a href="#environment" id="environment"></a>

When preparing your environment:

* Use reliable tools such as **Hardhat**, **Foundry**, or **Anvil**.
* Specify both the **RPC endpoint** and the **exact block number** used for the fork.
* Keep the setup completely local. The PoC should never send transactions or move funds.
* Replicate real contract states as accurately as possible to show the vulnerability in a safe and controlled setting.

***

### Implementation <a href="#implementation" id="implementation"></a>

Each PoC should be **runnable, minimal, and self-contained**. Reviewers should be able to reproduce it easily by following the included instructions.

To make your PoC clear and reproducible:

* Include all configuration and dependency files (for example, `package.json`, `foundry.toml`, or environment setup).
* Use environment variables such as `RPC_URL` and `BLOCK_NUMBER` instead of embedding sensitive data directly in the code.
* Add concise **comments and print statements** to describe each major step:
  * Setting up the forked environment
  * Triggering the condition or running the query
  * Displaying the observable outcome
* Ensure the console output clearly shows the point where the vulnerability or query condition is confirmed.
* Focus only on what is necessary to reproduce the issue. Avoid unrelated code or complex setup steps.
* If useful, include a short explanation of the potential impact (for example, total affected tokens multiplied by the average 7-day price).

***

### Submission Format <a href="#submission-format" id="submission-format"></a>

Every PoC submission should contain the following elements:

1. **Runnable code** — preferably a single script or test file that executes from start to finish.
2. **Run instructions** — step-by-step commands explaining how to start the local fork and execute the PoC.
3. **Expected output** — a short example of the results or console logs that should appear.
4. **Safety statement** — a note confirming that the PoC runs only in a local fork and does not interact with live networks.
5. **Configuration files** — all necessary files and dependencies required to run the PoC.
6. _(Optional)_ A link to a GitHub repository or Google Drive folder if the PoC consists of multiple files.

***

### Safety and Compliance <a href="#safety-and-compliance" id="safety-and-compliance"></a>

PoCs must always be conducted responsibly and in accordance with contest rules.\
To keep testing environments secure and compliant:

* Never interact with mainnet, testnets, or production systems.
* Do not use private keys, seed phrases, or any sensitive credentials.
* Avoid actions that could result in fund movement or state modification.
* Submit only complete, reproducible PoCs. Theoretical or partial examples will not be accepted.
* Follow all official Glider Query Contest policies and related security guidelines.

***

A clear and reproducible PoC is one of the most valuable parts of your submission.\
It demonstrates technical accuracy, shows that your query truly detects a real vulnerability, and allows reviewers to verify your findings safely and confidently.
