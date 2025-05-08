# 🎓 Glider: The Basics

## What Is Glider

Glider is a scalable code analyzer designed to help security researchers, developers, and more scan for code patterns, bugs, and code usage in Solidity contracts deployed on an EVM chain. Users can write Glider queries, using Glider API to identify the code they are looking for.

## Types of Glider Queries

How you write a Glider query depends on your goal. While there are many ways to write a query, queries can broadly be categorized into two types: **targeting specific vulnerabilities** or **gathering broader insights**.

### 1. Specific Vulnerability Queries

These queries are designed to help security researchers identify specific vulnerabilities by minimizing the number of results. This is achieved by filtering out false positives and tailoring the query to target specific edge cases. A smaller, more precise result set allows researchers to quickly identify vulnerabilities.

### 2. Code Pattern and Statistical Queries

These queries focus on identifying broader trends, such as common code patterns or statistical insights. Here, the priority is not on individual results but on gathering a larger dataset to observe overall patterns. These queries are designed to be less focused on specific code scenarios and more on abstract code usage.

## How Glider Works

The Glider language, a subset of Python, is what powers these queries. If you understand Python, then you can begin writing Glider queries.&#x20;

When a user writes a Glider query, they can submit it to the Glider engine for processing. The Glider engine executes the query against the Glider database, which contains every verified (or matching one) Solidity contract deployed on-chain. If any matching results are found, they are returned to the user.

## Purpose of Course

This course is designed to teach beginners how to write basic Glider queries. We will go over Glider basics, such as debugging and creating filters. Then, we will cover various Glider components that will help you solidify writing Glider queries: Instructions, Functions, and Contracts.&#x20;

Each section will consist of exercises that let users build a query from scratch. By the end of the section, the user will have completed a query that will identify specific code patterns or vulnerabilities. If you ever feel stuck, don’t worry! We’ve included solutions for each exercise that you can reference to get back on track or to confirm your answers.

The final section includes several bonus challenges to help you further sharpen your Glider skills. We recommend exploring these challenges after completing the other sections.

## A Note on Foundational Queries

In the following sections, each section will introduce a foundational query. We refer to these queries as "foundational" as they will serve as essential building blocks for writing future Glider queries.

Mastering foundational queries will give you a strong base for creating more advanced and customized queries as you progress toward becoming a Glider expert!
