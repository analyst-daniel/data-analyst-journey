# SQL Fundamentals — Lesson 3: Aggregate Functions

**Date:** November 23, 2026  
**Topic:** Summarizing data with SQL

## 1. SQL query basics (review)

A SQL query can retrieve columns from a database table using `SELECT` and `FROM`. A semicolon (`;`) terminates the SQL statement.

```sql
SELECT column_1,
       column_2
FROM table_name;
```

## 2. What is data aggregation?

Aggregation summarizes multiple rows using functions such as `SUM()`, `AVG()`, and `COUNT()`. Instead of looking at raw records one by one, aggregated results help reveal useful patterns and overall metrics.

## 3. Aggregate functions covered

| Function | Purpose |
| --- | --- |
| `SUM(column)` | Adds up values in a column |
| `AVG(column)` | Calculates the average |
| `MIN(column)` | Finds the minimum value |
| `MAX(column)` | Finds the maximum value |
| `COUNT(column)` | Counts non-NULL values in a column |
| `COUNT(DISTINCT column)` | Counts unique non-NULL values |
| `COUNT(*)` | Counts rows |

## 4. Multiple summary metrics in a single query

Use commas to combine multiple aggregate functions within one `SELECT` statement. Aliases made with `AS` make the resulting column names easier to understand.

```sql
SELECT COUNT(order_id)          AS order_count,
       COUNT(DISTINCT user_id)  AS user_count,
       SUM(amount)              AS revenue,
       AVG(amount)              AS avg_amount
FROM orders;
```

This query calculates four metrics from the `orders` table:
- `order_count`: number of non-NULL `order_id` values;
- `user_count`: number of distinct, non-NULL `user_id` values;
- `revenue`: total amount;
- `avg_amount`: average amount.

The values themselves are not shown in the lesson materials, so this is a query example rather than a recorded result.

## 5. Plan the aggregation before writing SQL

Before writing a summary query, answer two questions:

1. **Which column should I summarize?** Choose the field relevant to the analytical question.
2. **Which aggregate function should I use?** Match the operation to the information needed (total, average, minimum, maximum, or count).

## Suggested independent practice (not yet verified)

- [ ] Calculate the total of an amount column with `SUM()`.
- [ ] Calculate an average using `AVG()`.
- [ ] Find the smallest and largest values using `MIN()` and `MAX()`.
- [ ] Compare `COUNT(column)` with `COUNT(DISTINCT column)`.
- [ ] Write one query containing at least four aggregate functions and readable aliases.
- [ ] Explain what question each resulting metric answers.

**Learning status:** Lesson materials reviewed and recorded. Independent exercises have not been verified.

*Based on six screenshots shared for the November 23, 2026 lesson. The NULL and COUNT(*) distinctions are additional technical clarifications, not claims made by the screenshots.*
