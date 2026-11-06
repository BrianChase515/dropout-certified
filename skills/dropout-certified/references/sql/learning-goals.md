# Data Analysis with SQL v1: learning goals

Version 1, November 2026. These are exactly what the exam tests. Queries are written in standard SQL as supported by SQLite, which is free and runs everywhere; almost everything carries over to PostgreSQL, MySQL, SQL Server and BigQuery.

Each goal has an ID (for example `SQL4.3`) that practice exercises, exam tasks and progress tracking all refer to.

| Domain | Weight |
|---|---|
| SQL1. Data fundamentals | 10% |
| SQL2. Retrieving and filtering | 15% |
| SQL3. Aggregating | 20% |
| SQL4. Joining tables | 20% |
| SQL5. Advanced querying | 20% |
| SQL6. Analysis and communication | 15% |

## SQL1. Data fundamentals (10%)

- **SQL1.1** Read a schema: tables, columns, data types, primary keys and foreign keys, and what one row of each table represents (its grain).
- **SQL1.2** Explain how a database table differs from a spreadsheet, and when each is the better tool.
- **SQL1.3** Recognize dirty data: duplicates, inconsistent spellings and case, stray spaces, numbers or dates stored as text, impossible values.
- **SQL1.4** Explain what NULL means (unknown or missing, not zero or empty text) and how it behaves in comparisons and arithmetic.
- **SQL1.5** Store and compare dates as ISO text (`YYYY-MM-DD`) and explain why that format sorts correctly.

## SQL2. Retrieving and filtering (15%)

- **SQL2.1** Select columns, rename them with `AS`, and compute new columns with arithmetic and string functions.
- **SQL2.2** Filter rows with `WHERE` using comparisons, `AND`/`OR`/`NOT` with correct parentheses, `IN`, `BETWEEN` and `LIKE`.
- **SQL2.3** Filter correctly around NULL with `IS NULL` / `IS NOT NULL`, and use `COALESCE` to supply defaults.
- **SQL2.4** Sort with `ORDER BY` on several columns and directions, and take the top rows with `LIMIT`, including ties.
- **SQL2.5** Remove duplicates with `DISTINCT`, and know when duplicates mean a data problem instead.
- **SQL2.6** Clean values in a query: `TRIM`, `LOWER`/`UPPER`, `REPLACE`, `CAST`, and `ROUND`.

## SQL3. Aggregating (20%)

- **SQL3.1** Use `COUNT`, `SUM`, `AVG`, `MIN` and `MAX`, including how each treats NULL, and the difference between `COUNT(*)`, `COUNT(column)` and `COUNT(DISTINCT column)`.
- **SQL3.2** Group with `GROUP BY` on one or more columns, and explain why every selected column must be grouped or aggregated.
- **SQL3.3** Filter groups with `HAVING`, and explain how it differs from `WHERE`.
- **SQL3.4** Compute rates and shares correctly: avoid integer division, and choose the right denominator.
- **SQL3.5** Group by derived values: months from dates, buckets from `CASE`, cleaned categories.

## SQL4. Joining tables (20%)

- **SQL4.1** Write inner joins on keys, with table aliases, across two or more tables.
- **SQL4.2** Use `LEFT JOIN` to keep unmatched rows, and explain why a `WHERE` condition on the right table can silently turn it into an inner join.
- **SQL4.3** Find rows with no match (customers with no orders) using `LEFT JOIN ... IS NULL` or `NOT EXISTS`.
- **SQL4.4** Recognize fan-out: joining to a "many" table multiplies rows and inflates sums and counts, and fix it by aggregating before joining or counting distinct keys.
- **SQL4.5** Join a table to itself, and join on conditions other than equality (date ranges, price bands).
- **SQL4.6** Combine result sets with `UNION` and `UNION ALL`, and know the difference.

## SQL5. Advanced querying (20%)

- **SQL5.1** Use subqueries in `WHERE`, `FROM` and `SELECT`, including `IN` and `EXISTS`.
- **SQL5.2** Structure multi-step logic with common table expressions (`WITH`).
- **SQL5.3** Write `CASE` expressions for categories, conditional counts and conditional sums.
- **SQL5.4** Use window functions: `ROW_NUMBER`, `RANK`, `DENSE_RANK`, `LAG`/`LEAD`, and running totals with `SUM() OVER (... ORDER BY ...)`.
- **SQL5.5** Pick the top N per group, and compute change from the previous period.
- **SQL5.6** Work with dates: extract year and month with `strftime`, compute differences in days, and group by period.

## SQL6. Analysis and communication (15%)

- **SQL6.1** Translate a business question into precise definitions before writing SQL: what counts as an active customer, which dates, which statuses.
- **SQL6.2** Sanity-check results: row counts, totals that reconcile, spot checks of individual records, and results that are suspiciously round or large.
- **SQL6.3** Avoid misleading comparisons: different time windows, survivorship, small samples, averages hiding skew (use the median or distribution when it matters).
- **SQL6.4** State a finding clearly: the number, what it means, how it was calculated, and its main caveat, in a few sentences a manager can act on.
- **SQL6.5** Use AI to help write SQL responsibly: give it the schema, check its query on the real data, and never trust a result you haven't verified.
