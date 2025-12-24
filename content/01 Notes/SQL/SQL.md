# What is SQL?
- **SQL** (Structured Query Language) is a programming language used to manage and manipulate relational databases.
- It provides a standardised way to interact with databases, allowing users to store, retrieve, update, and delete data.
- SQL is used in various applications such as web development, data analysis, and backend systems.
# What is a Database?
- A database is an organized collection of data, stored and retrieved digitally from a remote or local computer system. Databases can be vast and complex and such databases are developed using fixed design and modeling approaches.
# What are constraints in SQL?
- Constraints are used to specify the rules concerning data in the table. The constraints are:
  - NOT NULL -> Restricts NULL value from being inserted into a column
  - CHECK -> Verifies values in a field satisfy a condition
  - UNIQUE -> Ensures unique values to be inserted in the field
  - PRIMARY KEY -> Uniquely identifies each record in a table
  - FOREIGN KEY -> Ensures referential integrity for a record in other table
# What is Primary Key?
- The PRIMARY Key constraint uniquely identifies each row in a table. It must contain unique values and has an implicit not null constraint. A table in SQL is strictly restricted to have one and only one primary key.
# What is the SELECT statement?
- SELECT operator in SQL is used to retrieve data from a database. The data returned is stored in a result table called the result-set.
- **SYNTAX:** SELECT * FROM table.name
# What is SQL?

- **SQL** stands for Structured Query Language. It is the standard language for relational database management systems. Handles organized data comprised of entities and relations.
# What are Tables and Fields?
- A tables is an organized collection of data stored in the form of rows and columns. Columns can be categorized as fields and the rows can be referred to as records.
# What is a View?
- A **VIEW** in SQL is a virtual table based on the result set of an SQL statement. A view contains rows and columns, just like a real table.
# What is the difference between DELETE, DROP and TRUNCATE?
- **DELETE** -> deletes rows based on a given condition
- **DROP** -> the entire table and rows are dropped along with the table schema
- **TRUNCATE** -> deletes all rows from the table but not the table schema
# What is pattern matching in SQL?

- SQL pattern matching provides for pattern search in data if you have no clue as to what word should it be. The **LIKE** operator is used in conjunction with SQL wildcards to fetch the required information.
  **%** --> represents zero, single or multiple characters
  **\_** --> represents a single character

# Basic Commands
## SELECT
- Select data from database
## FROM
- 

# Understanding Databases & Tables
- A **database** is a structured collection of data organised into tables, each consisting of rows and columns.
- Each row in a table represents a specific instance or record, and each column holds a specific type of data.
# DQL, DDL, and DML
- **DQL (Data Query Language)** is used for retrieving data with SELECT statements
- **DDL (Data Definition Language)** is used for defining and managing the structure of the database with CREATE, ALTER, and DROP statements.
- **DML (Data Manipulation Language)** is used for manipulating data with INSERT, UPDATE, and DELETE statements.

---
[[SQL by Code with Harry]]
