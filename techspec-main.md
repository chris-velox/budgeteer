# Budgeteer

## Goals

Create a "single page" application similar to Quicken, MoneyDance, or MoneyDance. The intent is to provide transaction tracking, budget tracking, reporting and visualizations.

## Overall Technical Specs

The application will consist of:

- Frontend interface for accepting user input and displaying results. The frontend will make API calls to the backend to retrieve and store data.
- Backend interface for receiving API calls to retrieve and store data. The backend will also provide the logical and arithmetic functions needed for the frontend. The backend will also provide the interface to the database for persistent storage. (FastAPI + SQLModel)

The backend should support multiple encrypted databases. (SQLModel)

- Sqlite3 + SQLCipher
- MySQL/MariaDB
- PostgreSQL

### Potential Needs

- Caching DB like Redis?
- Analytics DB like DuckDB to speed up visualizations and reports?
