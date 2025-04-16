# Budgeteer Data

## Goal

The data layer of budgeteer stores the data for the app. The data has to support personal transaction tracking for different types of accounts and transactions.

## Entities

### Institutions

Each institution record has the following fields:

- id: uuid (primary key) - required
- institution name: string - required
- institution routing number: string - store encrypted - optional
- institution web site: url - optional

future fields:

- institution connection type: enumerated list

### Accounts

Each account record has the following fields:

- id: uuid (primary key) - required
- account name: string - required
- account number: string - stored encrypted - optional
- account type: enumerated list - required
  - savings
  - checking
  - credit
  - loan
  - investment
  - asset
  - liability
- account visibility: shown/hidden - required
- display group: uuid (foreign key) - required - default depends on account type selected
- institution (foreign key) - required

### Display Groups

The Display Group is used to organize accounts in the account list navigator. Each Display Group record has the following fields:

- id: uuid (primary key)
- display group name: string
- display group order: integer

### Account Transactions

Each Account Transaction has the following fields:

- id: uuid (primary key) - required
- payee: string - required
- transaction date: date - required
- check number: integer - optional
- tags: tags - optional
- status: enumerated list - required
  - uncleared (default)
  - cleared
  - reconciled
  - scheduled
- amount: currency - required
- memo: text - optional

### Transaction Split

Transaction Splits are individual component transactions contained in an Account Transaction. If an Account Transaction has a single Transaction Split, the Category is displayed in the register and the Account Transaction Account is equal to the Transaction Split amount.

Each Transaction Split has the following fields:

- id: uuid (primary key) - required
- account transaction id: uuid (foreign key) - required
- transfer id: uuid (foreign key) - optional (two-way link)
- category: uuid (foreign key) - required
- amount: currency - required

### Payees

The Payees table captures the list of previously entered Payees. Each Payee has the following fields:

- id: uuid (primary key) - required
- payee: string - required

### Categories

The Categories list contains a nested list of categories. Each category has the following fields:
