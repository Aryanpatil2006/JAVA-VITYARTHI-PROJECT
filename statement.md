# Project Statement

**Project title:** ABC Bank – Account Management System
**Student:** Aryan Patil
**Registration No.:** 25BAI10768
**University:** VIT Bhopal University
**Course:** Programming in Java

---

## Problem Statement

Small branches, clubs, cooperatives and training environments often track customer accounts on paper or in loose spreadsheets. This leads to four recurring problems:

- Duplicate or mistyped account numbers.
- Balances that are changed without any check, so withdrawals can exceed the available money.
- No simple way to restrict withdrawals to someone who knows a secret code.
- Data that disappears or has to be re-entered because it is not saved in a consistent place.

There is a need for a small, easy-to-use desktop application that lets a clerk manage accounts reliably, enforces basic banking rules, and keeps the data between sessions, without needing a database server or an internet connection.

## Proposed Solution

ABC Bank is a Java Swing desktop application that provides a graphical ledger for managing customer accounts. It validates all input, protects withdrawals with a 4-digit PIN, and saves the ledger to a file in the user's home folder using Java object serialization.

## Objectives

1. Provide a clear GUI for opening, closing, finding and listing accounts.
2. Support deposits and withdrawals with rules that prevent invalid amounts and overdrafts.
3. Require a correct 4-digit PIN before any withdrawal.
4. Reject duplicate account numbers and non-numeric or empty input.
5. Persist data between runs, with a save prompt on exit.
6. Use only the standard Java library so the program runs on any machine with a JDK.

## Target Users

- Bank clerks or front-desk staff at a small branch or society
- Students learning object-oriented programming and GUI development in Java
- Instructors who need a compact example of Swing, collections and file I/O working together

## Scope

**Included:**

- Account creation and closure
- Deposit and withdrawal
- PIN setup and verification
- Account search and a table of all accounts
- Dashboard with account count and total balance
- Saving and loading the ledger

**Not included:**

- Transaction history or statements
- Transfers between accounts
- Interest calculation
- Multiple user roles or login
- Database or network features

## Key Features

| Feature | Description |
|---|---|
| Dashboard | Number of open accounts and total balance |
| Open / Close Account | Add or remove accounts with validation |
| Deposit | Adds a positive amount to an account |
| Withdraw | Needs account number, PIN and amount; blocks overdrafts |
| Set PIN | Sets or changes a 4-digit PIN with confirmation |
| Find Account | Shows one account's details (PIN hidden) |
| All Accounts | Read-only table of every account |
| Save Ledger | Writes data to `~/ABCBank/accounts.dat` |
| Status bar | Shows the result of every action |

## Technology Stack

| Item | Choice |
|---|---|
| Language | Java (JDK 8 or later) |
| GUI | Swing (`javax.swing`, `java.awt`) |
| Data structure | `LinkedHashMap<String, Accounting>` |
| Storage | Java serialization (`ObjectOutputStream` / `ObjectInputStream`) |
| External libraries | None |

## Expected Outcome

A working, portable desktop application that lets a user manage accounts end to end: open an account, set a PIN, deposit, withdraw, look up balances, save the ledger, and find the same data when the program is started again.

## Limitations

- PINs are stored in plain text in the data file.
- There is no lock-out after repeated wrong PIN attempts.
- Money is stored as `double` rather than `BigDecimal`.
- Opening balances are not checked for negative values.

See `README.md` for usage instructions and the project report for the full design and test cases.
