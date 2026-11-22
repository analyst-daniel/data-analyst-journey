# SQL Fundamentals — November 22, 2026

## 1. Select columns

Use `SELECT` to specify which columns to retrieve and `FROM` to identify the source table.

```sql
SELECT column_1
FROM table_1;
```

```sql
SELECT column_1, column_2
FROM table_1;
```

```sql
SELECT *
FROM table_1;
```

The asterisk (`*`) selects every column.

## 2. Sort rows

Use `ORDER BY` to sort query results by a column.

```sql
SELECT column_1, column_2
FROM table_1
ORDER BY column_1 DESC;
```

- `ASC` means ascending order (A–Z or smallest to largest). This is the default when no direction is provided.
- `DESC` means descending order (Z–A or largest to smallest).

## 3. Limit returned rows

Use `LIMIT` to restrict how many rows the query returns.

```sql
SELECT *
FROM table_1
LIMIT 10;
```

`LIMIT` appears at the end of these basic queries. Without `ORDER BY`, the specific rows returned are not guaranteed to be in a meaningful order.

### Combined example

```sql
SELECT column_1, column_2
FROM table_1
ORDER BY column_1 DESC
LIMIT 10;
```

This returns up to ten rows, ordered by `column_1` from highest to lowest.

## 4. Temporary query results

- A `SELECT` query returns a result set without changing the original data.
- The results reflect a snapshot of the data queried at that moment.
- Save or export a result if it needs to be kept for later use.

## 5. Handling SQL errors

- SQL syntax must be precise.
- Read error messages and check spelling, punctuation, and the order of clauses.
- Practice makes syntax errors easier to spot and correct.

## Practice checklist

- [ ] Select one column without hints.
- [ ] Select multiple columns without hints.
- [ ] Select all columns using `*`.
- [ ] Sort ascending and descending.
- [ ] Return the first ten rows using `LIMIT`.
- [ ] Combine `ORDER BY` and `LIMIT`.
- [ ] Identify and fix an intentionally broken query.

*Source: lesson notes shared on November 22, 2026. The examples are illustrative; the checklist does not claim exercises have been completed.*
