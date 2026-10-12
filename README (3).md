# ABC Bank – Account Management System

A desktop banking ledger built with **Java Swing**. Open and close accounts, deposit and withdraw money, protect withdrawals with a 4-digit PIN, and keep everything saved between sessions. No external libraries or database needed.

> Course project – *Programming in Java*, VIT Bhopal University
> Author: Aryan Patil (Reg. No. 25BAI10768)

---

## Features

- **Dashboard** – number of open accounts and total balance at a glance
- **Open Account** – account number, holder name and opening balance (duplicates are rejected)
- **Close Account** – remove an account from the ledger
- **Deposit** – add funds to an existing account
- **Withdraw** – requires the account's 4-digit PIN; blocks overdrafts
- **Set PIN** – set or change a PIN (exactly 4 digits, entered twice)
- **Find Account** – look up one account by number (the PIN is never shown)
- **All Accounts** – table of every account with a Refresh button
- **Save Ledger / Exit** – manual save, plus a Yes / No / Cancel save prompt on exit
- Status bar that reports the result of every action

## Requirements

- **JDK 8 or later** (check with `java -version` and `javac -version`)
- A desktop environment (Windows, macOS or Linux)

## Getting Started

1. Put `BankApp.java` in an empty folder. The file name must be exactly `BankApp.java`.
2. Open a terminal in that folder and compile:

   ```bash
   javac BankApp.java
   ```

3. Run:

   ```bash
   java BankApp
   ```

You can also open the file in any IDE (IntelliJ IDEA, Eclipse, VS Code with the Java extension, NetBeans) and run the `main` method of `BankApp`.

## How to Use

1. **Open an account** from the sidebar: enter an account number, name and opening balance.
2. **Set a PIN** for the account. A PIN is required before the first withdrawal.
3. **Deposit** and **Withdraw** using the account number (and the PIN for withdrawals).
4. Use **Find Account** or **All Accounts** to check balances.
5. Click **Save Ledger** (or choose *Yes* when exiting) so your data is kept for next time.

### Example walkthrough

| Step | Screen | Input |
|---|---|---|
| 1 | Open Account | `101`, `Asha`, `5000` |
| 2 | Set PIN | `101`, `4321`, `4321` |
| 3 | Deposit | `101`, `1500` → balance `6500.00` |
| 4 | Withdraw | `101`, PIN `4321`, `1000` → balance `5500.00` |
| 5 | Save Ledger | data written to disk |

## Where Is My Data Stored?

The ledger is saved to `ABCBank/accounts.dat` inside your home folder:

| OS | Path |
|---|---|
| Windows | `C:\Users\<you>\ABCBank\accounts.dat` |
| macOS / Linux | `~/ABCBank/accounts.dat` |

The folder is created automatically on the first save. To start fresh, close the app and delete `accounts.dat`.

> **Note:** If you change the fields of the `Accounting` class later, old `accounts.dat` files may no longer load (Java serialization). Delete the file when that happens.

## Project Structure

```
BankApp.java
├── class Accounting      – data model (account no., name, balance, PIN); Serializable
└── class BankApp         – JFrame with the GUI and all logic
    ├── Sidebar           – navigation buttons
    ├── CardLayout area   – Home, Create, Delete, Deposit, Withdraw, Set PIN, Find, View All
    ├── Status bar        – feedback messages
    └── File logic        – loadAccounts(), saveAccounts(), handleExit()
```

**Key design choices**

- `LinkedHashMap<String, Accounting>` stores accounts: fast lookup by account number and stable display order.
- `CardLayout` switches between panels without opening extra windows.
- Object serialization (`ObjectOutputStream`) saves and restores the ledger.
- `user.home` is used for the data path so the program is portable.

## Input Rules

| Field | Rule |
|---|---|
| Account number | Not empty; must be unique |
| Balance / amount | Must be a number; deposit and withdrawal amounts must be greater than zero |
| PIN | Exactly 4 digits and must match the confirmation |
| Withdrawal | PIN must be set and correct; amount cannot exceed the balance |

## Troubleshooting

- **`class BankApp is public, should be declared in a file named BankApp.java`** – rename the file to `BankApp.java`.
- **`javac` is not recognized** – install a JDK (not just a JRE) and add it to your PATH.
- **Colours or fonts look different** – the app uses Georgia, Segoe UI and Consolas; other systems substitute similar fonts. On macOS the system look-and-feel may draw sidebar buttons in a native style.
- **"Could not read the existing ledger file"** – the data file is damaged or from an older version of the code. Delete `accounts.dat` and restart.

## Known Limitations

- PINs are stored in plain text in the data file.
- No limit on wrong PIN attempts.
- No transaction history or transfers between accounts.
- Opening balance is not checked for negative values.
- Money is stored as `double` (a real banking system would use `BigDecimal`).

## Possible Improvements

- Hash PINs and lock accounts after repeated failures
- Transaction history and account-to-account transfers
- `BigDecimal` for money values
- Split the code into model / view / controller classes and add unit tests
- Store data in a database (SQLite via JDBC)

## Documentation

A full project report accompanies this code (abstract, design, module description, test cases, limitations and future work).

## License

Created for academic purposes. Free to use and modify for learning.
