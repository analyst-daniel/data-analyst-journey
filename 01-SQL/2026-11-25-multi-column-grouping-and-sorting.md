# SQL Fundamentals — Lesson 5: Multi-Column Grouping and Sorting

**Date:** November 25, 2026  
**Topic:** Grouping by multiple dimensions, sorting by multiple columns, and interpreting grouped results.

## 1. From one grouping column to several

An overall summary calculates aggregate metrics for the entire table. Adding `GROUP BY category` produces a separate result for each category:

```sql
SELECT category,
       COUNT(order_id)         AS order_count,
       COUNT(DISTINCT user_id) AS user_count,
       SUM(amount)             AS revenue,
       AVG(amount)             AS avg_amount
FROM orders
GROUP BY category;
```

To analyze every category within each location, include both columns in `SELECT` and `GROUP BY`:

```sql
SELECT category,
       location,
       COUNT(order_id)         AS order_count,
       COUNT(DISTINCT user_id) AS user_count,
       SUM(amount)             AS revenue,
       AVG(amount)             AS avg_amount
FROM orders
GROUP BY category, location;
```

Each result row represents a distinct combination of category and location present in the data.

## 2. Grouping by column positions

SQL dialects that support positional grouping let you refer to selected columns by their positions:

```sql
SELECT location,
       category,
       COUNT(order_id)         AS order_count,
       COUNT(DISTINCT user_id) AS user_count,
       SUM(amount)             AS revenue,
       AVG(amount)             AS avg_amount
FROM orders
GROUP BY 1, 2;
```

Here `1` refers to `location` and `2` refers to `category`. Writing the column names explicitly is usually easier to maintain if the selection order changes. Positional references are not supported in every SQL context or dialect.

## 3. Choosing the right level of detail

The lesson showed an example grouping by five dimensions:

```sql
SELECT location,
       category,
       order_month,
       customer_segment,
       payment_method,
       COUNT(order_id)         AS order_count,
       COUNT(DISTINCT user_id) AS user_count,
       SUM(amount)             AS revenue,
       AVG(amount)             AS avg_amount
FROM orders
GROUP BY location, category, order_month, customer_segment, payment_method;
```

More dimensions produce more detailed combinations, but also more rows to review and often fewer observations per group. The lesson's illustrative scenario had up to **96 possible groups**, each with four metrics—up to **384 metric values**. Fewer groups appear when some combinations do not occur.

**Practical rule:** Only group by dimensions needed to answer the analytical question. Including group size (such as `COUNT(order_id)`) helps evaluate how much data supports each result. Small groups may have unstable summary statistics; they are not automatically invalid.

## 4. Missing groups: do not jump to conclusions

A combination such as `UK` + `Grocery` may not appear in a grouped result. The lesson identified three possible explanations:

1. **Lost data or a query issue:** Relevant records were missing or filtered out.
2. **No activity:** The combination is possible but no transactions occurred.
3. **Impossible combination:** The category is not offered at that location.

A missing group does not, by itself, prove zero demand. Investigate the cause before drawing a conclusion.

## 5. Sorting by multiple columns

The order of expressions in `ORDER BY` establishes sorting priority.

To display each location's categories together and list its highest-revenue categories first:

```sql
SELECT location,
       category,
       COUNT(order_id)         AS order_count,
       COUNT(DISTINCT user_id) AS user_count,
       SUM(amount)             AS revenue,
       AVG(amount)             AS avg_amount
FROM orders
GROUP BY location, category
ORDER BY location ASC, revenue DESC;
```

- **First sort key:** `location ASC` groups the location labels in alphabetical order.
- **Second sort key:** `revenue DESC` sorts the categories within each location from highest to lowest revenue.

The lesson also illustrated `ORDER BY revenue DESC, location ASC`. That reverses the priority: it primarily ranks *all rows* by revenue and only uses location to break revenue ties. It does **not** keep each location's categories together.

## 6. Example: average fare by city and ride type

```sql
SELECT city,
       ride_type,
       AVG(fare)      AS avg_fare,
       COUNT(trip_id) AS trip_count
FROM trips
GROUP BY city, ride_type
ORDER BY city ASC, avg_fare DESC;
```

This compares ride types within each city, showing higher average fares first. The trip count provides context for how many records contributed to each comparison.

## 7. Core lesson takeaways

- Multi-column `GROUP BY` supports multidimensional analysis.
- For basic aggregate queries, non-aggregated columns selected as group identifiers should also appear in `GROUP BY`.
- Every added grouping dimension can increase the number of distinct groups but does not necessarily do so.
- Smaller groups mean fewer observations supporting their metrics.
- Missing category combinations require investigation, not automatic assumptions.
- Multi-column `ORDER BY` uses the first expression as the primary sort, followed by subsequent tie-breakers.
- Keep the clause order: `SELECT` → `FROM` → `GROUP BY` → `ORDER BY`.

## Suggested independent practice — not yet assessed

- [ ] Group orders by both category and location.
- [ ] Rewrite `GROUP BY 1, 2` using explicit column names.
- [ ] Compare the number of groups for two versus five dimensions.
- [ ] Include group counts when comparing averages.
- [ ] Explain three possible causes of a missing category/location combination.
- [ ] Sort locations alphabetically, then their categories by descending revenue.
- [ ] Explain the difference between `ORDER BY location, revenue DESC` and `ORDER BY revenue DESC, location`.
- [ ] Group trips by city and ride type, then sort by city and average fare.

**Learning status:** Lesson reported as completed; independent proficiency and study duration have not been verified.

*Source: 17 screenshots supplied for the November 25, 2026 session. Clarifying notes distinguish the two sorting orders and qualify interpretation of small groups.*
