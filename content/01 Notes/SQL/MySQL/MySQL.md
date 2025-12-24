In MySQL, it follows a structure on which you have to write code otherwise you will get syntax error and the structure is:
- SELECT
- FROM
- WHERE
- ORDER BY

## Cheatsheet for direct use
```sql
-- This is a comment in SQL
SELECT -- used to select the columns
FROM -- used to select the table from the worksheet
AS -- used for alias
DISTINCT -- used for removing duplicates
AND -- only print when both conditions are met
OR -- print when either one of the conditions are met
IN -- it extracts the value passed on it
BETWEEN -- it extracts value between two conditions
LIKE -- it matches the value either in the start or in the end
^ -- to represent beginning of the string
$ -- to represent end of the string
| -- logical OR
[abcd] -- matches from the brackets
[-] -- matches from the range given
IS NULL -- it shows the specific column where there is null present
LIMIT -- it comes always at the end of the code
INNER JOIN -- used to join tables that are present inside a workspace
WHERE -- filter query to match a condition
ON -- used to join the tables
LEFT JOIN / RIGHT JOIN -- used to join tables that are present outside a workspace
CASE -- Return value on a specified condition
COMMIT -- Write transaction to a database
ROLLBACK -- Rollback the transaction
BEGIN -- Start a transaction
ALTER TABLE -- Add/Remove columns from table
UPDATE -- Update table data
CREATE -- Create TABLE, DATABASE, INDEX or VIEW
DELETE -- Delete rows from table
INSERT -- Add single row to table
DROP -- Delete TABLE, DATABASE, INDEX or VIEW
GROUP BY -- Group data into logical sets
ORDER BY -- Set order of result, Use DESC to reverse order
HAVING -- Same as WHERE but filters groups
COUNT -- Count number of rows
SUM -- Return sum of column
AVG -- Return average of column
MAX -- Return maximum value of column
MIN -- Return minimum value of column
```



> **AND operator is in top priority then OR operator and NOT operator**
> - AND
> - OR
> - NOT

We use % to denote that it can contain n number of values.

`%b` → it means value that ends with b

`%b%` → it means it can start with n number of values and then b and then ends with n number of values

`b%` → it means that the value starts with b

`_b` → it means that the value has two value and one is b and other one can be any value

We use database name (e.g., sql_store.items) for referencing the items table present in the sql_store database to avoid any errors

## Inner Joins

```sql
SELECT *
FROM orders
JOIN customers ON orders.customer_id = customers.customer_id
```

## Joining Across Databases

```sql
SELECT *
FROM order_items oi
JOIN sql_inventory.products p ON oi.product_id = p.product_id
```

## Self Joins

```sql
SELECT *
FROM employees e
JOIN employees m ON e.reports_to = m.employee_id
```

## Joining Multiple Tables

```sql
USE sql_store;

SELECT *
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN order_statuses os ON o.status = os.order_status_id
```

## Compound Join Conditions

```sql
SELECT *
FROM order_items oi
JOIN order_items_notes oin ON oi.order_id = oin.order_id AND oi.product_id = oin.product_id
```

## Implicit Join Syntax

```sql
-- Normal Syntax
SELECT *
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id

-- Implicit Join Syntax
SELECT *
FROM orders o, customers c
WHERE o.customer_id = c.customer_id
```

## Outer Joins

```sql
-- There are two outer JOIN -> LEFT & RIGHT
-- Depends on the tables you are joining
SELECT *
FROM orders o
LEFT JOIN customers c ON o.customer_id = c.customer_id

SELECT *
FROM orders o
RIGHT JOIN customers c ON o.customer_id = c.customer_id
```

<aside> 💡 A tip: `use only LEFT or RIGHT JOIN for easy readability`

</aside>

## Outer Joins between Multiple Tables

```sql
SELECT *
FROM orders o
LEFT JOIN customers c ON o.customer_id = c.customer_id
LEFT JOIN shippers sh ON o.shipper_id = sh.shipper_id
```

## Self Outer Joins

```sql
-- It will also output manager name in outer join as he reports to None.
USE sql_hr;

SELECT e.employee_id, e.first_name, m.first_name AS manager
FROM employees e
LEFT JOIN employees m ON e.reports_to = m.employee_id
```

## The USING Clause

```sql
-- In this clause we don't need to use ON when two columns have same name
-- You can use USING in both INNER and OUTER JOINS
SELECT *
FROM customers c
JOIN orders o USING (customer_id)
LEFT JOIN shippers sh USING (shipper_id)
```

## Natural Joins

```sql
-- Natural Joins are easier to write but produces complexity
SELECT o.order_id, c.first_name
FROM orders o
NATURAL JOIN customers c
```

## Cross Joins

```sql
-- There are IMPLICIT and EXPLICIT syntax

-- IMPLICIT SYNTAX
SELECT *
FROM customers c, orders o
ORDER BY c.first_name

-- EXPLICIT SYNTAX
SELECT *
FROM customers c
CROSS JOIN products p
ORDER BY c.first_name
```

## Unions

```sql
-- You need to use same number of columns to use union or else it will throw error
-- Whichever query you have above the column name would be named after it
SELECT first_name
FROM customers

UNION

SELECT name
FROM shippers

-- Exercise Solution
SELECT customer_id, first_name, points, 'BRONZE' AS type
FROM customers
WHERE points < 2000
UNION
SELECT customer_id, first_name, points, 'SILVER' AS type
FROM customers
WHERE points BETWEEN 2000 AND 3000
UNION
SELECT customer_id, first_name, points, 'GOLD' AS type
FROM customers
WHERE points > 3000
ORDER BY first_name
```

## Column Attributes

Use gear sign to see all the attributes present in the column

- PK → Primary Key
- NN → Not Null
- AI → Auto Increment
- UQ → Unique Index
- UN → Unsigned
- ZF → Zero Fill
- G → Generated Column
- DEFAULT/EXPRESSION → Need to provide a value which SQL takes by default

## Inserting a Single Row

```sql
INSERT INTO customers -- which table you want to insert to
VALUES ( -- Values to be added in the table
	DEFAULT,
    'Namya',
    'Shah',
    '2000-12-23',
    NULL,
    'Bopal',
    'Ahmedabad',
    'GJ',
    DEFAULT)
```

## Inserting Multiple Rows

```sql
INSERT INTO shippers (name)
VALUES ('Shipper1'), ('Shipper2'), ('Shipper3')
```

## Inserting Hierarchical Rows

```sql
INSERT INTO orders (customer_id, order_date, status) -- Parent
VALUES (2, '2019-06-06', 2);

INSERT INTO order_items -- Child
VALUES (LAST_INSERT_ID(), 4, 6, 4.2),
		(LAST_INSERT_ID(), 3, 5, 3.4)
```

## Creating a Copy of a Table

```sql
-- This copies everything from the orders table to orders_archived table
-- Primary Key and Auto Increment are unchecked by default
CREATE TABLE orders_archived AS SELECT * FROM orders

-- Copying only required data from orders table
INSERT INTO orders_archived
SELECT *
FROM orders
WHERE order_date < '1990-01-01'

-- Exercise Solution
CREATE TABLE invoices_archived AS
SELECT i.invoice_id, i.number, c.name AS client, i.invoice_total, i.payment_total, invoice_date, payment_date, due_date
FROM invoices i
JOIN clients c USING (client_id)
WHERE payment_date IS NOT NULL
```

To delete everything in the table and not the table use `truncate table` option

## Updating a Single Row

```sql
-- Using Hard Code
UPDATE invoices
SET payment_total = 10, payment_date = '1990-03-01'
WHERE invoice_id = 1

-- Removing mistakes and restoring default values
UPDATE invoices
SET payment_total = DEFAULT, payment_date = NULL
WHERE invoice_id = 1

-- Using Soft Code
UPDATE invoices
SET payment_total = invoice_total*0.5, payment_date = due_date
WHERE invoice_id = 3
```

## Updating Multiple Rows

```sql
UPDATE invoices
SET payment_total = invoice_total*0.5, payment_date = due_date
WHERE client_id IN (3,4)
```

<aside> 💡 MySQL Workbench throws error if you try to update multiple rows. If you want to make it work in MySQL Workbench then follow the following steps: `Preferences → SQL Editor → Other → Uncheck Safe Updates Option` and press OK

</aside>

## Using Subqueries in Updates

```sql
-- Updating single item using subquery
UPDATE invoices
SET payment_total = invoice_total*0.5, payment_date = due_date
WHERE client_id = (SELECT client_id FROM clients WHERE name = 'Myworks')

-- Updating multiple item using subquery
UPDATE invoices
SET payment_total = invoice_total*0.5, payment_date = due_date
WHERE client_id IN (SELECT client_id FROM clients WHERE state IN ('CA', 'NY'))
```

```sql
-- Exercise Solution
-- Orders table
-- No comment
-- Update comments with more than 3000 points regard them as gold customer

UPDATE orders
SET comments = 'Gold Customer'
WHERE customer_id IN (SELECT customer_id FROM customers WHERE points > 3000)
```

## Deleting Rows

```sql
DELETE FROM invoices
WHERE client_id = (SELECT * FROM clients WHERE name = "Myworks")
```

## Offset Function

```sql
SELECT *
FROM customers
WHERE customers.points > 1000
ORDER BY customers.first_name
LIMIT 10 OFFSET 2
# Offset tells the database to return from which value
```

## Aggregate Functions

```sql
COUNT() -- Returns the number of rows in a database table
SUM() -- Returns the total sum of a numeric column
AVG() -- Calculates the average of a set of values
MIN() -- Returns the lowest value (minimum) in a set of non-NULL values
MAX() -- Returns the highest value (maximum) in a set of non-NULL values
```
