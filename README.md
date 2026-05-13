# TrelloTestingDB – Database Testing Project

**DEPI Graduation Program · Team B · E-Commerce Project**

---

## Project Overview

This repository contains the database testing work completed by Team B as part of the DEPI graduation program. The project focuses on validating the backend MySQL database (`TrelloTestingDB`) used in an E-Commerce application modeled around a Trello-style task management system.

The database was tested systematically across all CRUD operations, constraint enforcement, data integrity, and relational join queries using MySQL Workbench.

---

## Purpose of This Testing Iteration

The goal of this iteration was to verify that the database schema and its data behave correctly and safely under various conditions, including:

- Normal data operations (insert, read, update, delete)
- Boundary and edge cases (empty strings, special characters, non-existent IDs)
- Constraint enforcement (primary keys, foreign keys, NOT NULL rules)
- Referential integrity across related tables

---

## What Was Tested

The test suite covers **7 sections** with **38 total test cases**:

| Section | Coverage |
|---|---|
| Schema Verification | Table existence and column structure |
| Insert Tests (CREATE) | Valid inserts, edge cases, batch inserts |
| Constraint Violation Tests | Duplicate PKs, NULL values, invalid FKs, blocked deletes |
| Select Tests (READ) | Single row, all rows, empty results, JOIN queries |
| Update Tests | Field updates, partial updates, soft-delete flag |
| Delete Tests | Valid delete, confirm deletion, non-existent ID |
| Data Integrity Checks | Orphan detection, API test case record validation |

---

## Test Results Summary

| Metric | Value |
|---|---|
| Total Test Cases | 38 |
| Passed | 32 |
| Expected to Fail (Constraint Tests) | 6 |
| Overall Coverage | 100% |

> The 6 constraint test cases (DB_TC_12 – DB_TC_17) are intentionally designed to trigger database errors. Receiving the expected MySQL error code is the passing condition for each of those cases.

---

## Types of Testing Used

- **Functional Testing** – verifying CRUD operations work as expected
- **Negative Testing** – confirming the database rejects invalid inputs correctly
- **Boundary Testing** – edge cases like empty strings and special characters
- **Integration Testing** – JOIN queries validating relationships across tables
- **Data Integrity Testing** – checking for orphaned records and broken references

---

## Database Schema

The database contains four tables:

```
Boards
  └── Lists (FK: BoardID)
        └── Cards (FK: ListID)

TestCases (standalone – stores API test results)
```

---

## How to Import and Run the Database

**Prerequisites:** MySQL Server and MySQL Workbench installed on your machine.

**Steps:**

1. Clone or download this repository.
2. Open **MySQL Workbench** and connect to your local MySQL instance.
3. Open the file `DEPI_DATABASE_SQL.sql` via **File → Open SQL Script**.
4. Click the lightning bolt (⚡) icon to run the full script — this will create the database, tables, and all test data.
5. To run individual test cases, locate the relevant comment block (e.g., `-- DB_TC_06`) and run only that section.

> **Note:** Constraint violation tests (DB_TC_12 – DB_TC_17) must be run **one at a time** and separately from the rest of the script, as they are designed to produce errors.

---

## Tools Used

- **MySQL** – Database engine
- **MySQL Workbench** – Query execution and schema visualization

---

## Team Members

| Name |
|---|
| Ali Mohamed |
| Ahmed Amgad |
| Ganna Abdelaleem |
| Roaa Mostafa |
| Hana Ahmed |
| Salma Ayman |

---

## Files in This Repository

| File | Description |
|---|---|
| `README.md` | This file – project overview and instructions |
| `DEPI_DATABASE_SQL.sql` | Full SQL script: schema creation, seed data, and all 38 test cases |
| `DEPI_DATABASE_REPORT.md` | Detailed test report with results for each test case |

---

*DEPI Graduation Project · Team B 
