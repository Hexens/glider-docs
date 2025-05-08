---
description: This page explains how the Glider UI works and what features it has
---

# 🔧 Glider Usage

## Using the Glider IDE

The **Glider IDE** is a user-friendly platform for writing and running queries on smart contracts. This guide gives an overview of its main features and how it works.

### Writing Queries and Viewing Output

* Glider offers a REPL-like interface divided into two main sections:
  *   **Left Panel**: This is where you write query code using the Monaco editor, the same editor used in VSCode, with support for various features.

      * To run your query, click the '**Run**' button at the top of the interface.



      <figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 13.35.53.png" alt=""><figcaption></figcaption></figure>

      * During execution, errors may occur and will be displayed in the output window.



      <figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
  *   **Right Panel**: This panel displays the query output. Glider supports different output types.

      * **Contract**: When you return a contract, you get the contract address, which is a link to the contract's page on a scanner (like Etherscan), along with the contract's name.

      <figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

      * **Function**: When you return a function, you get the source code of the function, along with the address and name of the contract where it is defined.

      <figure><img src=".gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

      * **Instruction**: When you return an instruction, you get the source code of the function where the instruction is used. **GliderIDE** will automatically highlight the instruction in the function's source code. It also returns the address and name of the contract where the function is defined and used.

      <figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

      * **Print**: The print output appears in a separate window at the bottom of the output area, displaying any text you choose to print.

      <figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### Creating, Importing, and Sharing Queries

*   Above the **output** and **editor** windows, you can see three buttons: **New Query**, **Import** **Query**, and **Share**.

    * The **New Query** button allows you to create a new file for your query.
    * The **Import Query** button lets you import a query from a file on your local device.

    <figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 16.00.48.png" alt=""><figcaption></figcaption></figure>

    <figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 16.01.47.png" alt=""><figcaption></figcaption></figure>

    * **Share Query** is the most exciting feature. With this button, you can share your query via a link. When you press the **Share button**, a new link is generated for your query. Anyone with this link can view your query. You can share the link on X (formerly Twitter) or by clicking the 'Copy Link' button.

    <figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 16.01.09.png" alt=""><figcaption></figcaption></figure>

    <figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 16.01.38.png" alt=""><figcaption></figcaption></figure>

### Execution scope

* **Chain**: The first option allows you to run your query against an entire chain, which you can select from the integrated chain list. You also need access to run queries on the selected chain. The Kovan testnet is available to all users.

<figure><img src=".gitbook/assets/image (5).png" alt="" width="224"><figcaption></figcaption></figure>

* **Custom Scope**: This option allows users to run queries on smart contracts they upload. Note: This feature is still under development.

### Profile your query

**Next to the Run button, you'll find the Profile button, which displays the profiler results for your query**.

* **Performance Button**: Click this to open the performance window.

<figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 13.57.13 (1).png" alt=""><figcaption></figcaption></figure>

* **General Performance** results

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

* **Profile statistics**

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Query Explorer

* To create a new file, open the query explorer and click the '**`+`**'. This will create a file with a default name, which you can rename. By clicking the **folder icon**, you can create a folder in the same way as a file. To move a file into a folder, you have two options: first, click on the folder and then create the file inside it; second, create a file, click the '**`...`**' button, select '**Move File to Folder**', and choose the folder where you want to move it. From this menu, you can also delete, rename, or download files.

<figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 14.10.12.png" alt=""><figcaption></figcaption></figure>

* You can also download the entire output in **JSON** format by clicking the download button below the output window.

<figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 14.55.12.png" alt=""><figcaption></figcaption></figure>

Output json example:

```json
[
  {
    "contract": "0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e",
    "contract_name": "Address",
    "contract_link": "https://etherscan.io/address/0x9e35577836b8ac2e075a8d30e150bb9aafcbb64e",
    "uuid": "db1fd33e-4f81-4fc3-86db-c03c6923baac",
    "severity": "none",
    "sol_function": "function isContract(address account) internal view returns (bool) {\n        // This method relies on extcodesize/address.code.length, which returns 0\n        // for contracts in construction, since the code is only stored at the end\n        // of the constructor execution.\n\n        return account.code.length > 0;\n    }",
    "sol_instruction": "{\n        // This method relies on extcodesize/address.code.length, which returns 0\n        // for contracts in construction, since the code is only stored at the end\n        // of the constructor execution.\n\n        return account.code.length > 0;\n    }"
  },
  {
    ...
  },
  ...
]
```

### Documentation

* You can access the full Glider documentation from the Glider IDE by clicking the '**Guide**' button.

<figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 15.41.02.png" alt=""><figcaption></figcaption></figure>

After clicking the '**Guide**' button, a window will appear on the right side of the editor with the documentation. In this window, you can find everything available in the **GitBook** documentation. It also includes a search function, allowing you to search for specific functions. Additionally, you can access the full **GitBook** documentation by clicking the link near the search bar.

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

### Useful Links and Materials

In the **Glider IDE** header, you'll find several useful buttons and links.

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

* You'll find the '**Help**' button, which provides links to support resources, bug bounty guidelines, and the Glider documentation.

<figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 15.47.23.png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

* By clicking the **Discord** logo, you can join our **Discord** server, where you'll find channels for support, learning materials, and more.

<figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 15.49.03.png" alt=""><figcaption></figcaption></figure>

* In the Resources section, you'll find useful tools such as the **RVSS** **Calculator** (CVSS calculator for Web3), **Vulnerapedia**, Bug Bounty Guidelines, and the Glider Documentation.

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

* The '**My Scopes**' section is where you can use the custom scope features. As mentioned, this feature is still under development and will be available soon.
* If you click the rectangular button next to **Remedy** (highlighted in the red square in the screenshot), a dropdown will appear with other **Remedy** products, such as the **Remedy Bug Bounty platform** and **Engram** (ZK proof of text authority).

<figure><img src=".gitbook/assets/Screenshot 2025-01-07 at 15.54.44 (1).png" alt=""><figcaption></figcaption></figure>
