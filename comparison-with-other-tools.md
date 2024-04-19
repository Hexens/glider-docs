---
description: Glider, Semgrep, Solgrep, SAST
---

# 👥 Comparison with other tools

There are a variety of static analysis tools that one can use for security research purposes. In this page, we will compare Glider to some of the other tools mainly used by researchers.

## Semgrep/Solgrep

One of the static analysis tools that address the reusability, ease of use, and distribution aspects is Semgrep (also solgrep which is very similar).&#x20;

The main difference between Semgrep and Glider is that Semgrep works on the AST of the code and does not have the full potential to use Control Flow and Data Flow graphs of the code. Although Semgrep has taint mode, it is [limited](https://semgrep.dev/docs/writing-rules/data-flow/data-flow-overview/#design-trade-offs).&#x20;

It only allows declarative logic, while Glider gives the ability to write both declarative and imperative logic, making it much more flexible.

While benefiting from a shallow learning curve, it is limited in its functionality.

## Slither

In comparison to Semgrep, SAST tools like Slither can operate on CFG/DFG, do complex taint analysis, and so on, as well as it has well-designed IR (Intermediate Representation), moreover the Glider uses the SlithIR for intermediate representation. But the overall downside of these kind of tool is its learning curve as well as the inability to do the analysis on a scale, which affects both distribution and scalability aspects.
