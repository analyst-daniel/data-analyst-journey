# SQL Fundamentals — Lesson 4: GROUP BY and Grouped Aggregation

**Date:** November 24, 2026  
**Lesson topic:** Grouped aggregation, sorting aggregated results, and planning SQL queries.

## 1. Overall aggregation vs. grouped aggregation

An aggregate query without `GROUP BY` summarizes the entire data set:

```sql
SELECT COUNT(order_id)         AS order_count,
       COUNT(DISTINCT user_id) AS user_count,
       SUM(amount)             AS revenue,
       AVG(amount)             AS avg_amount
FROM orders;
```

With `GROUP BY`, the same metrics are calculated separately for each category. The result has one row per group:

```sql
SELECT category,
       COUNT(order_id)         AS order_count,
       COUNT(DISTINCT user_id) AS user_count,
       SUM(amount)             AS revenue,
       AVG(amount)             AS avg_amount
FROM orders
GROUP BY category;
```

This can reveal patterns and differences between categories that a single overall summary cannot show.

## 2. Sorting grouped results

Add `ORDER BY` after `GROUP BY` to sort the resulting groups.

```sql
SELECT category,
       COUNT(order_id)         AS order_count,
       COUNT(DISTINCT user_id) AS user_count,
       SUM(amount)             AS revenue,
       AVG(amount)             AS avg_amount
FROM orders
GROUP BY category
ORDER BY revenue DESC;
```

- `ORDER BY revenue` sorts by the revenue alias in ascending order by default.
- `ORDER BY revenue DESC` sorts from the highest revenue to the lowest.

## 3. Example: group trips by ride type

```sql
SELECT ride_type,
       SUM(fare)      AS revenue,
       AVG(fare)      AS avg_fare,
       COUNT(trip_id) AS trip_count
FROM trips
GROUP BY ride_type
ORDER BY trip_count DESC;
```

This query compares revenue, average fare and trip count by ride type, displaying the ride types with the highest number of recorded trips first.

## 4. Split–Apply–Combine

Grouped aggregation follows three conceptual steps:

1. **Split:** Divide the rows into groups based on distinct values of the grouping column.
2. **Apply:** Calculate aggregates separately for each group.
3. **Combine:** Return the groups and their calculated metrics as one summary table.

This is a conceptual explanation of what `GROUP BY` achieves.

## 5. Plan a grouped aggregation before writing SQL

Ask three questions:

1. **Which column defines the groups?** For example, `category` or `ride_type`.
2. **Which columns contain the values to summarize?** For example, `amount` or `fare`.
3. **Which aggregate functions answer the question?** For example, `COUNT()`, `SUM()`, `AVG()`, or `COUNT(DISTINCT ...)`.

One useful preliminary check is to inspect the categories present in the data:

```sql
SELECT DISTINCT category
FROM orders;
```

## 6. SQL clause order

For these queries, write clauses in this order:

```sql
SELECT grouping_column,
       SUM(amount) AS total_amount
FROM table_name
GROUP BY grouping_column
ORDER BY total_amount DESC;
```

The lesson also illustrated the conceptual processing sequence `FROM` → `GROUP BY` → `SELECT` → `ORDER BY`, which differs from the order in which SQL clauses are written.

## Independent practice checklist

- [ ] Explain the difference between total aggregation and grouped aggregation.
- [ ] Find all distinct category values before grouping.
- [ ] Calculate total revenue for each category.
- [ ] Add order count and average amount to the same grouped query.
- [ ] Sort groups by revenue in descending order.
- [ ] Summarize trips by ride type and order by trip count.
- [ ] Explain Split–Apply–Combine using the orders example.
- [ ] Write the correct SQL clause order without looking at notes.

**Learning status:** Lesson reported as completed. Independent practice has not yet been assessed.

*Based on the 13 lesson screenshots shared on November 24, 2026. The note on conceptual processing order distinguishes it from SQL syntax order; actual database query execution can be optimized and need not follow this literal sequence.*
