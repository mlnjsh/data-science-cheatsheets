# SQL Cheatsheet

## Basic Queries

```sql
SELECT col1, col2 FROM table WHERE condition;
SELECT DISTINCT col FROM table;
SELECT * FROM table ORDER BY col DESC LIMIT 10;
SELECT COUNT(*), AVG(col), SUM(col) FROM table;
```

## Filtering

```sql
WHERE col = 'value'
WHERE col IN ('a', 'b', 'c')
WHERE col BETWEEN 10 AND 20
WHERE col LIKE '%pattern%'
WHERE col IS NULL / IS NOT NULL
WHERE col1 > 5 AND (col2 = 'a' OR col3 < 10)
```

## JOINs

| Type | What it returns |
|------|----------------|
| `INNER JOIN` | Only matching rows from both tables |
| `LEFT JOIN` | All rows from left + matching from right |
| `RIGHT JOIN` | All rows from right + matching from left |
| `FULL OUTER JOIN` | All rows from both tables |
| `CROSS JOIN` | Cartesian product |

```sql
SELECT a.*, b.col
FROM table_a a
INNER JOIN table_b b ON a.id = b.a_id;
```

## GROUP BY

```sql
SELECT category, COUNT(*), AVG(price)
FROM products
GROUP BY category
HAVING COUNT(*) > 5
ORDER BY AVG(price) DESC;
```

## Window Functions

```sql
-- Row number, rank, dense rank
SELECT *, ROW_NUMBER() OVER (PARTITION BY dept ORDER BY salary DESC) as rn
FROM employees;

-- Running total
SELECT *, SUM(amount) OVER (ORDER BY date) as running_total
FROM transactions;

-- Moving average
SELECT *, AVG(value) OVER (ORDER BY date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) as ma7
FROM metrics;

-- Lead / Lag
SELECT *, LAG(value, 1) OVER (ORDER BY date) as prev_value
FROM metrics;
```

## CTEs (Common Table Expressions)

```sql
WITH ranked AS (
    SELECT *, RANK() OVER (PARTITION BY dept ORDER BY salary DESC) as rnk
    FROM employees
)
SELECT * FROM ranked WHERE rnk <= 3;
```

## Subqueries

```sql
-- In WHERE
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

-- In FROM
SELECT dept, avg_sal FROM (
    SELECT dept, AVG(salary) as avg_sal FROM employees GROUP BY dept
) sub WHERE avg_sal > 50000;
```

## Useful Patterns

```sql
-- Deduplicate
SELECT DISTINCT ON (email) * FROM users ORDER BY email, created_at DESC;

-- Pivot (PostgreSQL)
SELECT * FROM crosstab('SELECT row, col, val FROM table');

-- COALESCE (first non-null)
SELECT COALESCE(nickname, first_name, 'Unknown') as display_name FROM users;

-- CASE
SELECT CASE WHEN score >= 90 THEN 'A' WHEN score >= 80 THEN 'B' ELSE 'C' END as grade
FROM students;
```
