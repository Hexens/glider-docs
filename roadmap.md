---
description: >-
  This page describes the current functionality and future development
  milestones.
---

# 🗺️ Roadmap

Currently, Glider has the capability to run queries and do CFG/DFG analysis on a scale, but there is still a lot to do and to improve; this is not even version 1.0.

The main milestones we want to deliver in the foreseeable future:

* Add API functionality - there are some cases that the framework does not support currently. This is the first-class objective for the team to cover all of the possible scenarios, and the engine will be updated constantly to improve. Also, we are working on the API design in a way that it should become as easy to use as it can be; for this, Glider will be constantly updated with its user-friendly and shortcut functions that will help researchers describe complex scenarios without needing a PhD in code analysis.
* Move Graph module to API - in the current design, the dataflow and taint analysis features are heavily dependent on the Graph module of the framework (not API), which is less user-friendly. Our goal is to get rid of the need to use these functions.
* Storage Query - one of the major features in development is the ability to write storage/state queries and filters in the glide code as well. Imagine finding all non-conventional implementations of some ERC standards, searching for all contracts that interact with them and continuing analysis on that set.
* Integration with third-party toolings - as the Glider is using a Python environment, we plan to add integrations with other toolings that have interfaces accessible through Python. Researchers will be able to connect symbolic execution and fuzzing engines directly in the glides.
* CI/CD integration
* ...
* Many many more!
