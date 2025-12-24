- **Subqueries** also called a nested query or inner query is a query which is present inside another SQL query. In SQL, it is possible to place a SQL query inside another query. For example,
```sql
SELECT *
FROM Students
WHERE marks = (
	SELECT max(marks)
	FROM Students
);
```
In a subquery, the outer query's result is dependent on the result-set of the inner query. This is the reason why subqueries are also called nested queries.
### Example:
#### Main Query:
```sql
SELECT product_name FROM products
```
#### Subquery:
```sql
SELECT product_id FROM orders WHERE customer_id = 123
```
##### Description
- Retrieve names of products ordered by customer with ID 123.
## Types of Subqueries:
![[Screenshot_2024-07-12-10-06-10-20_1c337646f29875672b5a61192b9010f9.jpg]]
1. Single-row subquery: Returns a single value.
2. Multi-row subquery: Returns multiple rows.
3. Correlated subquery: References columns from outer query.
## Subquery Rules:
- Subqueries must be enclosed within parantheses.
- Subqueries always runs first followed by the main query.
- The subqueries in MySQL cannot use the ORDER BY keyword whereas the main query can use the ORDER BY keyword whenever required. You can use the GROUP BY command to perform the same function as the ORDER BY in the subquery.
- You cannot use BETWEEN operator within a SQL subquery. However, it can be used with the main query.
- It is not possible for subqueries to be enclosed in a set of functions.
## Benefits of using Subqueries
- Simplify complex queries
- Enable data comparison
- Enhance data retrieval flexibility
## Tips for using subqueries:
- Ensure subqueries return necessary data
- Optimize performance by limiting subquery executions
