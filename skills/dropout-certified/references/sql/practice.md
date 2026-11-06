# Practice exercises: Data Analysis with SQL

Run these against the practice database in `practice-db.md`. Try each one before looking at the answer. Answers were checked by running them; your query is right if it returns the same rows (column names can differ).

## P01 (SQL1.1, level 1)

How many rows are in each of the four tables?

<details><summary>Hint</summary>

Four small COUNT(*) queries, or one query with subqueries.

</details>

<details><summary>Answer</summary>

```sql
SELECT (SELECT COUNT(*) FROM customers), (SELECT COUNT(*) FROM products), (SELECT COUNT(*) FROM orders), (SELECT COUNT(*) FROM order_items)
```

Returns 1 row. First rows:

| 67 | 17 | 162 | 268 |

</details>

## P02 (SQL1.3, level 1)

List every distinct city value exactly as stored. How many different ways is the same city written?

<details><summary>Hint</summary>

SELECT DISTINCT, then look closely at spaces and capitals.

</details>

<details><summary>Answer</summary>

```sql
SELECT DISTINCT city FROM customers ORDER BY city
```

Returns 6 rows. First rows:

|  Miami |
| Austin |
| Detroit |

</details>

## P03 (SQL1.4, level 1)

How many customers have no segment recorded?

<details><summary>Hint</summary>

Missing values are NULL; `= NULL` never matches.

</details>

<details><summary>Answer</summary>

```sql
SELECT COUNT(*) FROM customers WHERE segment IS NULL
```

Returns 1 row. First rows:

| 2 |

</details>

## P04 (SQL2.1, level 1)

Show each product's name, its price, and its price with 8% sales tax added, rounded to 2 decimals, as a column called price_with_tax.

<details><summary>Hint</summary>

Arithmetic in the SELECT, then ROUND(..., 2) AS price_with_tax.

</details>

<details><summary>Answer</summary>

```sql
SELECT name, price, ROUND(price * 1.08, 2) AS price_with_tax FROM products ORDER BY name
```

Returns 17 rows. First rows:

| Camping Lantern | 30.14 | 32.55 |
| Cast Iron Pan | 44.02 | 47.54 |
| Chef Knife | 48.89 | 52.8 |

</details>

## P05 (SQL2.2, level 1)

List the Kitchen and Office products priced between $20 and $40, cheapest first.

<details><summary>Hint</summary>

IN for the categories, BETWEEN for the price.

</details>

<details><summary>Answer</summary>

```sql
SELECT name, category, price FROM products WHERE category IN ('Kitchen', 'Office') AND price BETWEEN 20 AND 40 ORDER BY price
```

Returns 4 rows. First rows:

| Herb Keeper | Kitchen | 22.21 |
| Cutting Board | Kitchen | 24.48 |
| Ergonomic Mouse | Office | 28.73 |

</details>

## P06 (SQL2.2, level 2)

List orders that are cancelled or refunded and were placed in 2026. Watch your parentheses.

<details><summary>Hint</summary>

AND binds tighter than OR, so group the status conditions.

</details>

<details><summary>Answer</summary>

```sql
SELECT order_id, order_date, status FROM orders WHERE (status = 'cancelled' OR status = 'refunded') AND order_date >= '2026-01-01' ORDER BY order_date
```

Returns 5 rows. First rows:

| 1130 | 2026-01-02 | cancelled |
| 1156 | 2026-02-22 | cancelled |
| 1053 | 2026-03-17 | cancelled |

</details>

## P07 (SQL2.3, level 2)

Show every customer's name and segment, displaying 'unknown' where the segment is missing.

<details><summary>Hint</summary>

COALESCE.

</details>

<details><summary>Answer</summary>

```sql
SELECT name, COALESCE(segment, 'unknown') AS segment FROM customers ORDER BY name
```

Returns 67 rows. First rows:

| Aiden Diallo | small_business |
| Ana Ito | small_business |
| Ana Jensen | consumer |

</details>

## P08 (SQL2.4, level 1)

Which 5 products have the highest list price?

<details><summary>Hint</summary>

ORDER BY ... DESC with LIMIT.

</details>

<details><summary>Answer</summary>

```sql
SELECT name, price FROM products ORDER BY price DESC LIMIT 5
```

Returns 5 rows. First rows:

| Hammock | 54.75 |
| Chef Knife | 48.89 |
| Monitor Stand | 48.82 |

</details>

## P09 (SQL2.6, level 2)

Show each customer's email cleaned up: no leading or trailing spaces, all lowercase. Leave out customers with no email.

<details><summary>Hint</summary>

TRIM and LOWER, plus IS NOT NULL.

</details>

<details><summary>Answer</summary>

```sql
SELECT name, LOWER(TRIM(email)) AS email FROM customers WHERE email IS NOT NULL ORDER BY name
```

Returns 63 rows. First rows:

| Aiden Diallo | aiden.diallo@mail.com |
| Ana Ito | ana.ito@mail.com |
| Ana Jensen | ana.jensen@inbox.net |

</details>

## P10 (SQL2.5, level 2)

How many customers live in each cleaned city? Show the city and the count, largest first.

<details><summary>Hint</summary>

Group by the cleaned expression, not the raw column.

</details>

<details><summary>Answer</summary>

```sql
SELECT LOWER(TRIM(city)) AS city, COUNT(*) AS customers FROM customers GROUP BY LOWER(TRIM(city)) ORDER BY customers DESC, city
```

Returns 4 rows. First rows:

| detroit | 25 |
| miami | 21 |
| portland | 12 |

</details>

## P11 (SQL3.1, level 2)

How many orders are there, how many distinct customers placed them, and how many customers have an email? Explain why the numbers differ.

<details><summary>Hint</summary>

COUNT(*), COUNT(DISTINCT customer_id), COUNT(email).

</details>

<details><summary>Answer</summary>

```sql
SELECT (SELECT COUNT(*) FROM orders), (SELECT COUNT(DISTINCT customer_id) FROM orders), (SELECT COUNT(email) FROM customers)
```

Returns 1 row. First rows:

| 162 | 60 | 63 |

</details>

## P12 (SQL3.2, level 2)

How many orders of each status were placed in each year? Show year, status and count.

<details><summary>Hint</summary>

strftime('%Y', order_date), and group by two columns.

</details>

<details><summary>Answer</summary>

```sql
SELECT strftime('%Y', order_date) AS year, status, COUNT(*) AS orders FROM orders GROUP BY year, status ORDER BY year, status
```

Returns 5 rows. First rows:

| 2025 | cancelled | 13 |
| 2025 | completed | 84 |
| 2025 | refunded | 7 |

</details>

## P13 (SQL3.3, level 2)

Which product categories have an average list price above $30?

<details><summary>Hint</summary>

HAVING filters groups after aggregation.

</details>

<details><summary>Answer</summary>

```sql
SELECT category, ROUND(AVG(price), 2) AS avg_price FROM products GROUP BY category HAVING AVG(price) > 30 ORDER BY avg_price DESC
```

Returns 3 rows. First rows:

| Outdoor | 33.47 |
| Office | 30.69 |
| Kitchen | 30.57 |

</details>

## P14 (SQL3.4, level 3)

What share of all orders were refunded, as a percentage to 1 decimal? Make sure you don't get 0.

<details><summary>Hint</summary>

Integer division: multiply by 100.0 first.

</details>

<details><summary>Answer</summary>

```sql
SELECT ROUND(100.0 * SUM(status = 'refunded') / COUNT(*), 1) AS refunded_pct FROM orders
```

Returns 1 row. First rows:

| 4.3 |

</details>

## P15 (SQL3.5, level 2)

How many customers signed up in each month? Show the month as YYYY-MM.

<details><summary>Hint</summary>

strftime('%Y-%m', signup_date).

</details>

<details><summary>Answer</summary>

```sql
SELECT strftime('%Y-%m', signup_date) AS month, COUNT(*) AS signups FROM customers GROUP BY month ORDER BY month
```

Returns 14 rows. First rows:

| 2025-01 | 4 |
| 2025-02 | 5 |
| 2025-03 | 2 |

</details>

## P16 (SQL4.1, level 2)

For each completed order, show the order id, the customer's name and the order date.

<details><summary>Hint</summary>

Join orders to customers on customer_id.

</details>

<details><summary>Answer</summary>

```sql
SELECT o.order_id, c.name, o.order_date FROM orders o JOIN customers c ON c.customer_id = o.customer_id WHERE o.status = 'completed' ORDER BY o.order_date, o.order_id
```

Returns 137 rows. First rows:

| 1060 | Hiro Ito | 2025-02-04 |
| 1035 | Quinn Alvarez | 2025-02-08 |
| 1074 | Maya Hughes | 2025-03-05 |

</details>

## P17 (SQL4.1, level 3)

Show total completed revenue for each product, highest first. Revenue is quantity times unit_price.

<details><summary>Hint</summary>

Three tables: order_items, orders (for status) and products (for the name).

</details>

<details><summary>Answer</summary>

```sql
SELECT p.name, ROUND(SUM(oi.quantity * oi.unit_price), 2) AS revenue FROM order_items oi JOIN orders o ON o.order_id = oi.order_id JOIN products p ON p.product_id = oi.product_id WHERE o.status = 'completed' GROUP BY p.product_id, p.name ORDER BY revenue DESC
```

Returns 15 rows. First rows:

| Hammock | 1634.29 |
| Monitor Stand | 1581.78 |
| Cast Iron Pan | 1096.12 |

</details>

## P18 (SQL4.2, level 3)

List every customer with their number of completed orders, including customers with none (show 0).

<details><summary>Hint</summary>

LEFT JOIN, and put the status condition in the ON clause, not WHERE.

</details>

<details><summary>Answer</summary>

```sql
SELECT c.name, COUNT(o.order_id) AS completed_orders FROM customers c LEFT JOIN orders o ON o.customer_id = c.customer_id AND o.status = 'completed' GROUP BY c.customer_id, c.name ORDER BY completed_orders DESC, c.name
```

Returns 67 rows. First rows:

| Ana Ito | 5 |
| Ana Patel | 5 |
| Bea Alvarez | 5 |

</details>

## P19 (SQL4.3, level 2)

Which products have never been ordered?

<details><summary>Hint</summary>

LEFT JOIN ... WHERE right side IS NULL, or NOT EXISTS.

</details>

<details><summary>Answer</summary>

```sql
SELECT p.name FROM products p WHERE NOT EXISTS (SELECT 1 FROM order_items oi WHERE oi.product_id = p.product_id) ORDER BY p.name
```

Returns 2 rows. First rows:

| Herb Keeper |
| Linen Napkins |

</details>

## P20 (SQL4.4, level 3)

A colleague counts customers per city with orders joined to order_items, and gets numbers bigger than the customer table. Write the correct count of customers per cleaned city who have at least one completed order.

<details><summary>Hint</summary>

The join to order_items repeats each customer once per item. Count DISTINCT customer_id.

</details>

<details><summary>Answer</summary>

```sql
SELECT LOWER(TRIM(c.city)) AS city, COUNT(DISTINCT c.customer_id) AS buying_customers FROM customers c JOIN orders o ON o.customer_id = c.customer_id AND o.status = 'completed' JOIN order_items oi ON oi.order_id = o.order_id GROUP BY LOWER(TRIM(c.city)) ORDER BY buying_customers DESC, city
```

Returns 4 rows. First rows:

| miami | 19 |
| detroit | 17 |
| portland | 10 |

</details>

## P21 (SQL4.5, level 3)

Find pairs of customers who signed up on the same day. Show each pair once.

<details><summary>Hint</summary>

Join customers to itself with a.customer_id < b.customer_id.

</details>

<details><summary>Answer</summary>

```sql
SELECT a.name, b.name, a.signup_date FROM customers a JOIN customers b ON a.signup_date = b.signup_date AND a.customer_id < b.customer_id ORDER BY a.signup_date
```

Returns 5 rows. First rows:

| Xin Lopez | Luis Lopez | 2025-02-02 |
| Xin Lopez | Maya Hughes | 2025-02-02 |
| Maya Hughes | Luis Lopez | 2025-02-02 |

</details>

## P22 (SQL4.6, level 2)

Make one list of all the distinct cleaned cities and all product categories, in a single column called label.

<details><summary>Hint</summary>

UNION removes duplicates; UNION ALL keeps them.

</details>

<details><summary>Answer</summary>

```sql
SELECT LOWER(TRIM(city)) AS label FROM customers UNION SELECT category FROM products ORDER BY label
```

Returns 8 rows. First rows:

| Home |
| Kitchen |
| Office |

</details>

## P23 (SQL5.1, level 2)

List products priced above the average list price.

<details><summary>Hint</summary>

A subquery in WHERE.

</details>

<details><summary>Answer</summary>

```sql
SELECT name, price FROM products WHERE price > (SELECT AVG(price) FROM products) ORDER BY price DESC
```

Returns 7 rows. First rows:

| Hammock | 54.75 |
| Chef Knife | 48.89 |
| Monitor Stand | 48.82 |

</details>

## P24 (SQL5.2, level 3)

Using a WITH clause, compute each customer's completed revenue, then show the average revenue per buying customer.

<details><summary>Hint</summary>

First CTE: revenue per customer. Then AVG over it.

</details>

<details><summary>Answer</summary>

```sql
WITH rev AS (SELECT o.customer_id, SUM(oi.quantity * oi.unit_price) AS r FROM orders o JOIN order_items oi ON oi.order_id = o.order_id WHERE o.status = 'completed' GROUP BY o.customer_id) SELECT ROUND(AVG(r), 2) AS avg_revenue_per_customer FROM rev
```

Returns 1 row. First rows:

| 205.6 |

</details>

## P25 (SQL5.3, level 2)

For each customer, count their completed, cancelled and refunded orders in three columns.

<details><summary>Hint</summary>

SUM(CASE WHEN ... THEN 1 ELSE 0 END), or SUM(status = '...').

</details>

<details><summary>Answer</summary>

```sql
SELECT c.name, SUM(o.status = 'completed') AS completed, SUM(o.status = 'cancelled') AS cancelled, SUM(o.status = 'refunded') AS refunded FROM customers c JOIN orders o ON o.customer_id = c.customer_id GROUP BY c.customer_id, c.name ORDER BY c.name
```

Returns 60 rows. First rows:

| Ana Ito | 5 | 2 | 0 |
| Ana Jensen | 1 | 0 | 0 |
| Ana Patel | 5 | 0 | 0 |

</details>

## P26 (SQL5.4, level 3)

Number each customer's orders in date order (1 = their first order).

<details><summary>Hint</summary>

ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY order_date, order_id).

</details>

<details><summary>Answer</summary>

```sql
SELECT customer_id, order_id, order_date, ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY order_date, order_id) AS nth_order FROM orders ORDER BY customer_id, nth_order
```

Returns 162 rows. First rows:

| 1 | 1004 | 2025-12-09 | 1 |
| 1 | 1005 | 2026-02-04 | 2 |
| 1 | 1002 | 2026-03-05 | 3 |

</details>

## P27 (SQL5.4, level 3)

Show completed revenue by month with a running total.

<details><summary>Hint</summary>

SUM(...) OVER (ORDER BY month) over a monthly aggregate.

</details>

<details><summary>Answer</summary>

```sql
WITH m AS (SELECT strftime('%Y-%m', o.order_date) AS month, SUM(oi.quantity * oi.unit_price) AS rev FROM orders o JOIN order_items oi ON oi.order_id = o.order_id WHERE o.status = 'completed' GROUP BY month) SELECT month, ROUND(rev, 2) AS revenue, ROUND(SUM(rev) OVER (ORDER BY month), 2) AS running_total FROM m ORDER BY month
```

Returns 17 rows. First rows:

| 2025-02 | 80.06 | 80.06 |
| 2025-03 | 127.19 | 207.25 |
| 2025-04 | 410.78 | 618.03 |

</details>

## P28 (SQL5.5, level 3)

For each customer, how many days passed between their first and second order? Only include customers with at least two orders.

<details><summary>Hint</summary>

LEAD or LAG over each customer's orders, then julianday() to subtract dates.

</details>

<details><summary>Answer</summary>

```sql
WITH o AS (SELECT customer_id, order_date, ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY order_date, order_id) AS n, LEAD(order_date) OVER (PARTITION BY customer_id ORDER BY order_date, order_id) AS next_date FROM orders) SELECT customer_id, CAST(julianday(next_date) - julianday(order_date) AS INTEGER) AS days_to_second FROM o WHERE n = 1 AND next_date IS NOT NULL ORDER BY customer_id
```

Returns 44 rows. First rows:

| 1 | 57 |
| 2 | 63 |
| 3 | 13 |

</details>

## P29 (SQL5.6, level 2)

How many days after signing up did each customer place their first order?

<details><summary>Hint</summary>

MIN(order_date) per customer, then julianday() difference.

</details>

<details><summary>Answer</summary>

```sql
SELECT c.name, CAST(julianday(MIN(o.order_date)) - julianday(c.signup_date) AS INTEGER) AS days_to_first FROM customers c JOIN orders o ON o.customer_id = c.customer_id GROUP BY c.customer_id, c.name, c.signup_date ORDER BY days_to_first
```

Returns 60 rows. First rows:

| Quinn Jensen | 0 |
| Tara Khan | 2 |
| Zoe Silva | 2 |

</details>

## P30 (SQL6.2, level 3)

Sanity check: does total completed revenue by category add up to total completed revenue overall? Write one query that shows both totals.

<details><summary>Hint</summary>

Compute both in subqueries and compare.

</details>

<details><summary>Answer</summary>

```sql
SELECT (SELECT ROUND(SUM(r), 2) FROM (SELECT SUM(oi.quantity * oi.unit_price) AS r FROM order_items oi JOIN orders o ON o.order_id = oi.order_id JOIN products p ON p.product_id = oi.product_id WHERE o.status = 'completed' GROUP BY p.category)) AS by_category, (SELECT ROUND(SUM(oi.quantity * oi.unit_price), 2) FROM order_items oi JOIN orders o ON o.order_id = oi.order_id WHERE o.status = 'completed') AS overall
```

Returns 1 row. First rows:

| 11307.98 | 11307.98 |

</details>

## P31 (SQL6.3, level 3)

Compare the average and the median completed order value. Why might they differ so much in this data?

<details><summary>Hint</summary>

Median: order the order totals and take the middle one. Look for an unusually large order.

</details>

<details><summary>Answer</summary>

```sql
WITH t AS (SELECT o.order_id, SUM(oi.quantity * oi.unit_price) AS tot FROM orders o JOIN order_items oi ON oi.order_id = o.order_id WHERE o.status = 'completed' GROUP BY o.order_id), r AS (SELECT tot, ROW_NUMBER() OVER (ORDER BY tot) AS rn, COUNT(*) OVER () AS n FROM t) SELECT ROUND((SELECT AVG(tot) FROM t), 2) AS average, ROUND(AVG(tot), 2) AS median FROM r WHERE rn IN ((n + 1) / 2, (n + 2) / 2)
```

Returns 1 row. First rows:

| 82.54 | 62.16 |

</details>

## P32 (SQL6.1, level 2)

Before writing any SQL: the boss asks for 'active customers last quarter.' Write down three questions you'd need answered first. Then answer it using: completed order in April to June 2026.

<details><summary>Hint</summary>

Which dates? Which statuses? Customers, or customers with revenue?

</details>

<details><summary>Answer</summary>

```sql
SELECT COUNT(DISTINCT customer_id) AS active_customers FROM orders WHERE status = 'completed' AND order_date BETWEEN '2026-04-01' AND '2026-06-30'
```

Returns 1 row. First rows:

| 15 |

</details>
