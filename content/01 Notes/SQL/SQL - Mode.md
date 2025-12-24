# Introduction
- SQL is used for accessing, cleaning, and analysing data that’s stored in databases.
- SQL (Structured Query Language) is a programming language designed for managing data in a relational database. It's been around since the 1970s and is the most common method of accessing data in databases today. SQL has a variety of functions that allow its users to read, manipulate, and change data. Though SQL is commonly used by engineers in software development, it's also popular with data analysts for a few reasons:
    - It's semantically easy to understand and learn.
    - Because it can be used to access large amounts of data directly where it's stored, analysts don't have to copy data into other applications.
    - Compared to spreadsheet tools, data analysis done in SQL is easy to audit and replicate. For analysts, this means no more looking for the [**cell with the typo in the formula**](http://www.washingtonpost.com/blogs/wonkblog/wp/2013/04/16/is-the-best-evidence-for-austerity-based-on-an-excel-spreadsheet-error/).
- SQL is great for performing the types of aggregations that you might normally do in an Excel pivot table—sums, counts, minimums and maximums, etc.—but over much larger datasets and on multiple tables at the same time.

# What’s a database?

A **database** is an organized collection of data.

# SQL LIMIT

## *Why should you limit your results?*

- Many analysts use limits as a simple way to keep their queries from taking too long to return. The aim of many of your queries will simply to be to see what a particular table looks like — you’ll want to scan the first few rows of data to get an idea of which fields you care about and how you want to manipulate them. If you query a very large table (such as one with hundreds of thousands or millions of rows) and don’t use a limit, you could end up waiting a long time for all of your results to be displayed, which doesn’t make sense if you only care about the first few.

> 📌 *Note: the clauses always need to be in this order: SELECT, FROM, WHERE.*

# SQL WHERE

## *How does WHERE work?*

- The SQL `WHERE` clause works in a plain-English way: the above query does the same thing as `SELECT * FROM tutorial.us_housing_units`, except that the results will only include rows where the `month` column contains the value `1`.
- In Excel, it’s possible to sort data in such a way that one column can be reordered without reordering any of the other columns — though that could badly scramble your data. When using SQL, entire rows of data are preserved together.

# SQL COMPARISON OPERATORS

## *Comparison operators on numerical data*

The most basic way to filter data is using comparison operators. The easiest way to understand them is to start by looking at a list of them:

| Equal to | = |
| --- | --- |
| Not equal to | <> or ≠ |
| Greater than | > |
| Less than | < |
| Greater than or equal to | ≥ |
| Less than or equal to | ≤ |

The comparison operators make the most sense when applied to numerical columns. For example, let’s use `>` to return only the rows where the West Region produced more than 30,000 housing units.

```sql
SELECT *
FROM tutorial.us_housing_units
WHERE west > 30
```

All of the above operators work on non-numerical data as well. `=` and `!=` make perfect sense — they allow you to select rows that match or don’t match any value, respectively.

```sql
SELECT *
FROM tutorial.us_housing_units
WHERE month_name != 'January'
```

There are some important rules when using these operators, though. If you’re using an operator with values that are non-numeric, you need to put the value in single quotes: `'value'`.

<aside>
💡 **Note:** SQL uses single quotes to reference column values.

</aside>

### *Comparison operators on non-numerical data*

```sql
SELECT *
FROM tutorial.us_housing_units
WHERE month_name != 'January'
```

- If you’re using an operator with values that are non-numeric, you need to put the value in single quotes: `'value'`


> 📌 **NOTE:** SQL uses single quotes to reference column values

# SQL Logical Operators

| LIKE | allows you to match similar values, instead of exact values |
| --- | --- |
| IN | allows you to specify a list of values you’d like to include |
| BETWEEN | allows you to select only rows within a certain range |
| IS NULL | allows you to select rows that contain no data in a given column |
| AND | allows you to select only rows that satisfy two conditions |
| OR | allows you to select rows that satisfy either of two conditions |
| NOT | allows you to select rows that do not match a certain condition |

## *SQL LIKE Operator*

`LIKE` is a logical operator in SQL that allows you to match on similar values rather than exact ones.

We use `ILIKE` function when we only know few things about the character

```sql
SELECT *
FROM tutorial.billboard_top_100_year_end
-- SQL LIKE
WHERE "group_name" LIKE 'drake'
-- SQL is a case sensitive language, so it will only 
-- return the answer that has lowercase drake in it.

-- SQL ILIKE
WHERE "group_name" ILIKE 'drake'
-- It will return all the rows that has drake in it
-- irrespective of typecase

-- SQL ILIKE with different function
WHERE "group_name" ILIKE 'drake%'
-- It will return all the rows that has drake in it
-- along with other string of characters (i.e., other
-- artists)
```

## *SQL IN Operator*

`IN` is a logical operator in SQL that allows you to specify a list of values that you’d like to include in the results.

**Examples:**

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year_rank IN (1, 2, 3)
```

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE artist IN ('Taylor Swift', 'Usher', 'Ludacris')
```

## *SQL BETWEEN Operator*

`BETWEEN` is a logical operator in SQL that allows you to select only rows that are within a specific range. It has to be paired with the `AND` operator.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year_rank BETWEEN 5 AND 10
```

`BETWEEN` includes the range bounds (in this case, 5 and 10) that you specify in the query, in addition to the values between them.

The above query will return the exact same results as the following query:

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year_rank >= 5 AND year_rank <= 10
```

## *SQL IS NULL Operator*

`IS NULL` is a logical operator in SQL that allows you to exclude rows with missing data from your results.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE artist IS NULL
```

## *SQL AND Operator*

`AND` is a logical operator in SQL that allows you to select only rows that satisfy two conditions.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year = 2012 AND year_rank <= 10
```

You can use SQL’s `AND` operator with additional `AND` statements or any other comparison operator, as many times as you want.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year = 2012
   AND year_rank <= 10
   AND "group_name" ILIKE '%feat%'
```

## *SQL OR Operator*

`OR` is a logical operator in SQL that allows you to select rows that satisfy either of two conditions.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year_rank = 5 OR artist = 'Gotye'
```

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year = 2013
   AND ("group_name" ILIKE '%macklemore%' OR "group_name" ILIKE '%timberlake%')
```

## *SQL NOT Operator*

`NOT` is a logical operator in SQL that you can put before any conditional statement to select rows for which that statement is false.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year = 2013
   AND year_rank NOT BETWEEN 2 AND 3
```

- Using `NOT` with `<` and `>` usually doesn’t make sense because you can simply use the opposite comparative operator instead.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year = 2013
   AND year_rank NOT > 3
-- This query return an error
```

- Instead write like this

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year = 2013
   AND year_rank <= 3
```

- `NOT` is commonly used with `LIKE`.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year = 2013
   AND "group_name" NOT ILIKE '%macklemore%'
```

- `NOT` is also frequently used to identify non-null rows, but the syntax is somewhat special — you need to include `IS` beforehand.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 WHERE year = 2013
   AND artist IS NOT NULL
```

## *SQL ORDER BY Operator*

The `ORDER BY` clause allows you to reorder your results based on the data in one or more columns.

```sql
SELECT *
  FROM tutorial.billboard_top_100_year_end
 ORDER BY artist
```

You’ll notice that the results are now ordered alphabetically from a to z based on the content in the `artist` column. This is referred to as ascending order, and it’s SQL’s default. If you order a numerical column in ascending order, it will start with smaller (or most negative) numbers, with each successive row having a higher numerical value than the previous.

```sql
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year = 2013
ORDER BY year_rank
```

- If you’d like your results in the opposite order (referred to as descending order), you need to add the `DESC` operator.

### *Ordering Data by Multiple Columns*

You can also order by multiple columns. This is particularly useful if your data falls into categories and you’d like to organize rows by date.

```sql
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year_rank <= 3
ORDER BY year DESC, year_rank
```

- You can see a couple things from the above query: First, columns in the `ORDER BY` clause must be separated by commas. Second the `DESC` operator is applied to the column that precedes it. **Finally, the results are sorted by the first column mentioned (year), then by `year_rank` afterward.**

## *Comments*

We use double dash (—) to comment in sql code.

# ***Intermediate SQL***

## *SQL Aggregate Functions*

- `COUNT` counts how many rows are in a particular column.
- `SUM` adds together all the values in a particular column.
- `MIN` and `MAX` return the lowest and highest values in a particular column, respectively.
- `AVG` calculates the average of a group of selected values.

## *SQL COUNT*

`COUNT` is a SQL aggregate function for counting the number of rows in a particular column. `COUNT` is the easiest aggregate function to begin with because verifying your results is extremely simple.

<aside>
💡 *Typing* `COUNT(1)` *has the same effect as* `COUNT(*)`.

</aside>

### Counting non-numerical columns

```sql
SELECT COUNT(date)
FROM tutorial.aapl_historical_stock_price
```

`COUNT` simply counts the total number of non-null rows, not the distinct values.

### Using Alias (AS)

Naming your columns so that they make a little more sense to anyone else who views your work.

```sql
SELECT COUNT(date) AS count_of_date
FROM tutorial.aapl_historical_stock_price
```

```sql
SELECT COUNT(date) AS "Count of Date"
FROM tutorial.aapl_historical_stock_price
```

<aside>
📌 *Note: This is really the only place in which you’ll ever want to use double quotes in SQL. Single quotes for everything else.*

</aside>

## *SQL SUM Function*

`SUM` is a SQL aggregate function, that totals the values in a given column. Unlike `COUNT`, you can only use `SUM` on columns containing numerical values.

```sql
SELECT SUM(volume)
  FROM tutorial.aapl_historical_stock_price
```

<aside>
📌 *An important thing to remember: **aggregators only aggregate vertically.**

You don’t need to worry as much about the presence of nulls with `SUM` as you would with `COUNT`, as `SUM` treats nulls as 0.*

</aside>

## *SQL MIN/MAX Functions*

`MIN` and `MAX` are SQL aggregation functions that return the lowest and highest values in a particular column.

They’re similar to `COUNT` in that they can be used on non-numerical columns. Depending on the column type, `MIN` will return the lowest number, earliest date, or non-numerical value as close alphabetically to “A” as possible. As you might suspect, `MAX` does the opposite — it returns the highest number, the latest date, or the non-numerical value closest alphabetically to “Z”.

```sql
SELECT MIN(volume) AS min_volume,
       MAX(volume) AS max_volume
  FROM tutorial.aapl_historical_stock_price
```

## *SQL AVG Function*

`AVG` is a SQL aggregate function that calculates the average of a selected group of values. It’s very useful, but has some limitations. First, it can only be used on numerical columns. Second, it ignores nulls completely.

```sql
SELECT AVG(high)
  FROM tutorial.aapl_historical_stock_price
 WHERE high IS NOT NULL

-- The above query produces same result as
SELECT AVG(high)
  FROM tutorial.aapl_historical_stock_price
```

## *SQL GROUP BY Function*

SQL aggregate function like `COUNT`, `AVG`, and `SUM` have something in common: they all aggregate across the entire table.

`GROUP BY` allows you to separate data into groups, which can be aggregated independently of one another.

```sql
 SELECT year,
       COUNT(*) AS count
  FROM tutorial.aapl_historical_stock_price
 GROUP BY year
```

### GROUP BY column numbers

As with `ORDER BY`, you can substitute numbers for column names in the `GROUP BY` clause. It’s generally recommended to do this only when you’re grouping many columns, or if something else is causing the text in the `GROUP BY` clause to be excessively long:

```sql
SELECT year,
       month,
       COUNT(*) AS count
  FROM tutorial.aapl_historical_stock_price
 GROUP BY 1, 2
```

*Note: this functionality (numbering columns instead of using names) is supported by Mode, but not every flavour of SQL, if you’re using another system or connected to certain types of databases, it may not work.*

### Using GROUP BY with ORDER BY

The order of column names in your `GROUP BY` clause doesn’t matter — the results will be the same regardless. If you want to control how the aggregations are grouped together, use `ORDER BY`.

```sql
SELECT year,
       month,
       COUNT(*) AS count
  FROM tutorial.aapl_historical_stock_price
 GROUP BY year, month
 ORDER BY month, year
```

### Using GROUP BY with LIMIT

SQL evaluates the aggregations before the `LIMIT` clause. If you don’t group any columns, you’ll get a 1-row result — no problem there. If you group by a column with enough unique values that it exceeds the `LIMIT` number, the aggregates will be calculated, and then some rows will simply be omitted from the results.

## *SQL HAVING*

```sql
SELECT year,
       month,
       MAX(high) AS month_high
  FROM tutorial.aapl_historical_stock_price
 GROUP BY year, month
HAVING MAX(high) > 400
 ORDER BY year, month
```

<aside>
📌 *Note:* `HAVING` *is the “clean” way to filter a query that has been aggregated, but this is also commonly done using a subquery.*

</aside>

### Query Clause Order

1. `SELECT`
2. `FROM`
3. `WHERE`
4. `GROUP BY`
5. `HAVING`
6. `ORDER BY`

## *SQL CASE*

The `CASE` statement is SQL’s way of handling if/then logic. The `CASE` statement is followed by at least one pair of `WHEN` and `THEN` statements — SQL’s equivalent of IF/THEN in Excel. Because of this pairing, you might be tempted to call this SQL `CASE WHEN`, but `CASE` is the accepted term.

Every `CASE` statement must end with the `END` statement. The `ELSE` statement is optional, and provides a way to capture values not specified in the `WHEN` / `THEN` statements.

```sql
SELECT player_name,
       year,
       CASE WHEN year = 'SR' THEN 'yes'
            ELSE NULL END AS is_a_senior
  FROM benn.college_football_players
```

In plain English, here’s what’s happening:

1. The `CASE` statement checks each row to see if the conditional statement — `year = 'SR'` is true.
2. For any given row, if that conditional statement is true, the word “yes” gets printed in the column that we have named `is_a_senior`.
3. In any row for which the conditional statement is false, nothing happens in that row, leaving a null value in the `is_a_senior` column.
4. At the same time all this is happening, SQL is retrieving and displaying all the values in the `player_name` and `year` columns.

The above query makes it pretty easy to see what’s happening because we’ve included the `CASE` statement along with the `year` column itself. You can check each row to see whether `year` meets the condition `year = 'SR'` and then see the result in the column generated using the `CASE` statement.

```sql
SELECT player_name,year,
CASE WHEN year = 'SR' THEN 'yes'
ELSE 'no' END AS is_a_senior  
FROM benn.college_football_players

```

### Adding multiple conditions to a CASE statement

You can also define a number of outcomes in a `CASE` statement by including as many `WHEN` / `THEN` statements.

```sql
SELECT player_name, weight,
CASE WHEN weight > 250 THEN 'over 250'
WHEN weight > 200 THEN '201-250'
WHEN weight > 175 THEN '176-200'
ELSE '175 or under' END AS weight_group
FROM benn.college_football_players
```

In the above example, the `WHEN` / `THEN` statements will get evaluated in the order that they’re written. So if the value in the `weight` column of a given row is 300, it will produce a result of “over 250”. Here's what happens if the value in the `weight` column is 180, SQL will do the following:

1. Check to see if `weight` is greater than 250. 180 is not greater than 250, so move on to the next `WHEN` / `THEN`
2. Check to see if `weight` is greater than 200. 180 is not greater than 200, so move on to the next `WHEN` / `THEN`
3. Check to see if `weight` is greater than 175. 180 is greater than 175, so record “175-200” in the `weight_group` column.

While the above works, it's really best practice to create statements that don't overlap. `WHEN weight > 250` and `WHEN weight > 200` overlap for every value greater than 250, which is a little confusing.

```sql
SELECT player_name, weight,
CASE WHEN weight > 250 THEN 'over 250'
WHEN weight > 200 AND weight <= 250 THEN '201-250'
WHEN weight > 175 AND weight <= 200 THEN '176-200'
ELSE '175 or under' END AS weight_group
FROM benn.college_football_players

```

### `CASE` Basics

1. The `CASE` statement always goes in the `SELECT` clause
2. `CASE` must include the following components: `WHEN`, `THEN`, and `END`. `ELSE` is an optional component.
3. You can make any conditional statement using any conditional operator (like `WHERE`) between `WHEN` and `THEN`. This includes stringing together multiple conditional statements using `AND` and `OR`.
4. You can include multiple `WHEN` statements, as well as an `ELSE` statement to deal with any unaddressed conditions. 

### Using `CASE` with aggregate functions

`CASE`'s slightly more complicated and substantially more useful functionality comes from pairing it with aggregate functions. For example, let’s say you want to only count rows that fulfil a certain condition. Since `COUNT` ignores nulls, you could use a `CASE` statement to evaluate the condition and produce null or non-null values depending on the outcome:

```sql
SELECT CASE WHEN year = 'FR' THEN 'FR'
            ELSE 'Not FR' END AS year_group,
            COUNT(1) AS count
  FROM benn.college_football_players
 GROUP BY CASE WHEN year = 'FR' THEN 'FR'
               ELSE 'Not FR' END
```

`WHERE` clause only allows you to count one condition. If you want to use multiple conditions then you need to `CASE` clause.

```sql
SELECT CASE WHEN year = 'FR' THEN 'FR'
            WHEN year = 'SO' THEN 'SO'
            WHEN year = 'JR' THEN 'JR'
            WHEN year = 'SR' THEN 'SR'
            ELSE 'No Year Data' END AS year_group,
            COUNT(1) AS count
  FROM benn.college_football_players
 GROUP BY year_group

-- The above code will be same as below

SELECT CASE WHEN year = 'FR' THEN 'FR'
            WHEN year = 'SO' THEN 'SO'
            WHEN year = 'JR' THEN 'JR'
            WHEN year = 'SR' THEN 'SR'
            ELSE 'No Year Data' END AS year_group,
            COUNT(1) AS count
  FROM benn.college_football_players
 GROUP BY CASE WHEN year = 'FR' THEN 'FR'
               WHEN year = 'SO' THEN 'SO'
               WHEN year = 'JR' THEN 'JR'
               WHEN year = 'SR' THEN 'SR'
               ELSE 'No Year Data' END
```

### Using `CASE` inside of aggregate functions

```sql
-- Data displayed above was vertical
SELECT CASE WHEN year = 'FR' THEN 'FR'
            WHEN year = 'SO' THEN 'SO'
            WHEN year = 'JR' THEN 'JR'
            WHEN year = 'SR' THEN 'SR'
            ELSE 'No Year Data' END AS year_group,
            COUNT(1) AS count
  FROM benn.college_football_players
 GROUP BY 1
 
 -- Data displayed in below code is horizontal
 SELECT COUNT(CASE WHEN year = 'FR' THEN 1 ELSE NULL END) AS fr_count,
       COUNT(CASE WHEN year = 'SO' THEN 1 ELSE NULL END) AS so_count,
       COUNT(CASE WHEN year = 'JR' THEN 1 ELSE NULL END) AS jr_count,
       COUNT(CASE WHEN year = 'SR' THEN 1 ELSE NULL END) AS sr_count
  FROM benn.college_football_players
```

## *SQL DISTINCT Clause*

You’ll occasionally want to look at only the unique values in a particular column. You can do this using `SELECT DISTINCT` syntax.

```sql
SELECT DISTINCT month
FROM tutorial.aapl_historical_stock_price
```

If you include two (or more) columns in a `SELECT DISTINCT` clause, your results will contain all of the unique pairs of those two columns.

```sql
SELECT DISTINCT year, month
  FROM tutorial.aapl_historical_stock_price
```
> 📌 *Note: You only need to include* `DISTINCT` *once in your* `SELECT` *clause — you do not need to add it for each column name.*

`DISTINCT` can be particularly helpful when exploring a new data set. In many real-world scenarios, you will generally end up writing several preliminary queries in order to figure out the best approach to answering your initial question.