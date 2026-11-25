# Learning Log

## 2026-11-22 — SQL fundamentals

**Study material:** Introductory SQL lesson notes (five slides).

**Topics covered:**
- Selecting one, multiple, or all columns with `SELECT`.
- Choosing the source table with `FROM`.
- Sorting query results with `ORDER BY`, ascending (`ASC`, default) or descending (`DESC`).
- Limiting the number of returned rows with `LIMIT`.
- Understanding that `SELECT` reads data without modifying the original table.
- Reading SQL syntax errors and checking queries for mistakes.

**Examples and explanations:** [SQL Fundamentals — 2026-11-22](01-SQL/2026-11-22-sql-fundamentals.md).

**Next practice goals:**
- Write queries selecting one, two, and all columns.
- Sort sample data in ascending and descending order.
- Combine `ORDER BY` and `LIMIT` to retrieve top results.
- Practice interpreting and fixing syntax errors.

**Progress note:** Topics recorded from lesson materials; independent mastery, study duration, and completed exercises have not yet been assessed.

## 2026-11-22 — SQL fundamentals, lesson 2

**Study material:** Five SQL lesson slides.

**Topics covered:**
- Using `SELECT DISTINCT` to retrieve unique values.
- Giving columns temporary, readable aliases with `AS`.
- Following SQL style conventions: uppercase keywords and descriptive `snake_case` aliases.
- Recognizing SQL dialects across different database systems.
- Understanding client-server architecture and how database clients connect to servers.

**Notes and examples:** [SQL Fundamentals — Lesson 2](01-SQL/2026-11-22-sql-fundamentals-lesson-2.md).

**Next practice goals:**
- Write a `SELECT DISTINCT` query independently.
- Rename a result column using `AS`.
- Apply consistent formatting to a complete SQL query.
- Explain client and server roles in a database system.

**Progress note:** Second lesson reported as completed. Exercises and practical proficiency have not yet been independently assessed.

## 2026-11-23 — SQL fundamentals, lesson 3: aggregation

**Study material:** Six lesson screenshots, including an example query using the `orders` table.

**Topics covered:**
- Reviewing `SELECT`, `FROM` and the semicolon statement terminator.
- Summarizing rows with aggregate functions.
- Using `SUM()`, `AVG()`, `MIN()`, `MAX()`, and `COUNT()`.
- Counting unique values using `COUNT(DISTINCT column)`.
- Combining multiple summary metrics in a single query with descriptive `AS` aliases.
- Planning an aggregation by deciding which column and which operation answer the analytical question.

**Notes and example query:** [SQL Fundamentals — Aggregate Functions](01-SQL/2026-11-23-aggregate-functions.md).

**Next practice goals:** Write a multi-metric summary query without prompts and explain the meaning of each metric.

**Progress note:** Lesson reported as completed; independent proficiency and study duration have not been verified.

## 2026-11-24 — SQL fundamentals, lesson 4: GROUP BY

**Study material:** Thirteen screenshots from the grouped aggregation lesson.

**Topics covered:**
- Comparing overall aggregation with grouped aggregation.
- Using `GROUP BY` to calculate metrics for each unique category.
- Combining `COUNT()`, `COUNT(DISTINCT ...)`, `SUM()` and `AVG()` with grouping.
- Sorting grouped results using `ORDER BY` and `DESC`.
- Analyzing order categories and trip types with grouped summary metrics.
- Understanding the Split–Apply–Combine concept.
- Using `SELECT DISTINCT` to inspect available grouping categories.
- Planning aggregations by selecting grouping fields, measured fields and aggregate functions.
- Writing SQL clauses in the correct order: `SELECT`, `FROM`, `GROUP BY`, `ORDER BY`.

**Notes and examples:** [SQL Fundamentals — GROUP BY and Grouped Aggregation](01-SQL/2026-11-24-group-by-aggregation.md).

**Next practice goals:** Independently calculate revenue, order count and average amount by category, sort the results by revenue, and explain the purpose of grouping.

**Progress note:** Lesson reported as completed. Independent exercises and study duration have not been verified.

## 2026-11-25 — SQL fundamentals, lesson 5: multi-column grouping and sorting

**Study material:** Seventeen screenshots covering multi-dimensional aggregation and result interpretation.

**Topics covered:**
- Grouping by more than one column, including `category` and `location`.
- Using multiple selected dimensions and the positional `GROUP BY 1, 2` syntax.
- Comparing detailed five-dimension grouping to simpler category-level summaries.
- Recognizing that excessive grouping can produce many rows and small sample sizes.
- Checking counts alongside aggregate metrics to assess reliability.
- Investigating missing category/location combinations instead of assuming zero demand.
- Sorting by multiple fields, with the first `ORDER BY` expression taking priority.
- Comparing revenue within locations using `ORDER BY location, revenue DESC`.
- Analyzing average fares and trip counts by city and ride type.

**Notes and query examples:** [SQL Fundamentals — Lesson 5](01-SQL/2026-11-25-multi-column-grouping-and-sorting.md).

**Next practice goals:** Build two-dimensional summaries, compare `ORDER BY` priorities, and explain how small or missing groups affect the interpretation of metrics.

**Progress note:** Lesson reported as completed; independent exercises and study duration have not been verified.
