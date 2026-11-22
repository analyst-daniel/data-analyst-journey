# SQL Fundamentals — Lesson 2 (November 22, 2026)

## 1. Find unique values with DISTINCT

Use `DISTINCT` immediately after `SELECT` to eliminate duplicate values from the query results.

```sql
SELECT DISTINCT column_name
FROM table_name;
```

## 2. Give columns aliases with AS

Aliases create temporary, more readable names in the result set. They do not rename the original columns in the database.

```sql
SELECT column_1 AS alias_name,
       column_2
FROM table_1;
```

Prefer clear, descriptive aliases and consistent `snake_case` naming.

## 3. SQL style conventions

Write SQL keywords in uppercase to distinguish them from table and column names. This is a readability convention, not a SQL syntax requirement.

```sql
SELECT employee_name AS full_name
FROM employees
ORDER BY full_name;
```

## 4. SQL dialects

Database systems use different SQL dialects. Their core syntax is similar, while some functions and features differ between platforms. Learning the fundamentals in one system helps when using others.

## 5. Client-server architecture

- Database servers store and manage databases.
- Database clients connect to servers and send SQL queries.
- Multiple users can connect to the same database server through different clients, including desktop programs and web applications.

## Practice checklist

- [ ] Use `SELECT DISTINCT` to return unique values from a column.
- [ ] Add a readable alias using `AS`.
- [ ] Write a query using uppercase keywords and `snake_case` aliases.
- [ ] Explain how a database client communicates with a database server.
- [ ] Describe why SQL syntax may vary across database systems.

**Progress note:** Lesson completed as reported; these practice exercises are not marked as independently verified.

*Based on the five lesson slides shared on November 22, 2026.*
