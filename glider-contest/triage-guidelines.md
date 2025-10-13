---
icon: book-heart
cover: ../.gitbook/assets/Glider QDB.png
coverY: 0
---

# Triage Guidelines

#### Who Are the Triagers?

Triagers are our Glider experts - experienced evaluators who ensure every submission is fairly and accurately reviewed. They are deeply familiar with the Glider engine and are responsible for maintaining the quality, safety, and integrity of all contest submissions.

***

### ⚙️ How Triage Works

Once you submit your entry to the Glider Contest, the triage process begins to evaluate and classify your submission.

#### Step-by-Step Flow

1.  **Contributing a Query to the Contest**\
    You can contribute your Glider query to the contest once it produces valid and meaningful results.

    Contributing means sharing your discovery with the Remedy triage team for evaluation and potential rewards.

    Before submitting, make sure your query runs successfully and demonstrates a real finding - not just theoretical logic.
2.  **Submission Received**

    When you submit, a dedicated thread is automatically opened with a triager. All discussions, clarifications, and updates regarding your submission will happen there.
3.  **Initial Review**

    The triager inspects your submission for correctness, clarity, and alignment with Glider’s contest goals. During this stage, they may provide feedback or request additional information.
4.  **Final Outcome**

    Once the review is complete, the triager assigns a status and, if applicable, an evaluation rating (see below).

***

### Submission Statuses

| Status    | Meaning                                                     | What You Can Do                        |
| --------- | ----------------------------------------------------------- | -------------------------------------- |
| Pending   | Submission is awaiting review.                              | You can still edit or update it.       |
| In Review | A triager is currently reviewing your submission.           | Editing is disabled during this phase. |
| Approved  | The submission is valid and accepted.                       | Celebrate! 🎉                          |
| Rejected  | The submission does not meet contest or technical criteria. | You may resubmit if rules allow.       |
| Outdated  | The submission is no longer relevant                        | Check newer Glider query version.      |
| On Halt   | Triager is rechecking the query                             | Wait for an update from the triager.   |

***

### 🧩 Contribution Type

Each submission must indicate its Contribution Type, helping triagers evaluate your intent and contribution scope:

| Type         | Description                                                                                                                                            |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| New Query    | Introduces a new vector — a completely new Glider query designed to detect a previously uncovered issue or pattern.                                    |
| Optimization | Enhances an existing query to make it safer, fresher, and more effective. Optimizations should detect more real issues while reducing false positives. |

***

### Evaluation Criteria

Once a submission is confirmed during the triage stage, the Remedy triager also provides a detailed assessment across several parameters.

This evaluation determines the rarity and value of the submission.

| Parameter       | Remedy’s Estimation                                                                                                                    |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Risk Likelihood | Likelihood of the vulnerability being exploited                                                                                        |
| Query Potential | Dynamic score that updates when the query finds new hits. At publication, it equals Initial Damage.                                    |
| Risk Impact     | Vulnerability impact, e.g. informational, low, medium, high, critical.                                                                 |
| Initial Damage  | Estimated financial damage that exploitation of vulnerable contracts found by the query could have caused at the time of contribution. |
| Remedy Opinion  | An average ranking of the opinions of Remedy triage team                                                                               |

Each parameter is typically rated on a 1–5 scale, and the overall profile of these ratings determines the rarity of the query:

Rarity Formula: `0,25 * Query Potential + 0,2 * (Risk Likelihood+Risk Impact+Initial Damage) +  0,15 *Remedy Opinion.`

| Rarity Level                                      | Rarity points | Meaning                                                                | Reward size |
| ------------------------------------------------- | ------------- | ---------------------------------------------------------------------- | ----------- |
| <mark style="color:$success;">**Uncommon**</mark> | 1.00–1.99     | <p>Possible bug severity:<br>Low, Informational</p>                    | Up to $50   |
| <mark style="color:blue;">**Rare**</mark>         | 2.00–2.94     | <p>Possible bug severity: Medium<br>(Or real word Low)</p>             | Up to $400  |
| <mark style="color:purple;">**Epic**</mark>       | 2.95–4.49     | <p>Possible bug severity: Critical, High<br>(Or real word Medium+)</p> | Up to $700  |
| <mark style="color:orange;">**Legendary**</mark>  | ≥4.50         | <p>Real-world high or critical<br>findings</p>                         | Up to $2000 |

***

### 🧭 Tips for Participants

* Clearly specify your Contribution Type - it helps triagers evaluate faster and more accurately.
* Keep your submission concise, well-documented, and reproducible.
* Watch for updates during the _Pending_ phase; once it moves to _In Review_, you can no longer edit.
* Remember: triagers are your allies — their feedback is aimed at strengthening your query and your standing in the contest.
