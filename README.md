# 🛒 Retail Store Relational Database & SQL Analytics

An end-to-end SQL database project built in **MySQL Workbench 8.0 CE** to model an e-commerce retail store and solve **42 business analytics tasks** across 6 difficulty tiers.

---

## 🏗️ 1. Database Schema (3NF)

Designed with primary keys, foreign keys, and integrity constraints across 6 tables:

* **`customers`**: Profiles, unique email addresses, and phone numbers.
* **`products`**: Product catalog, categories, positive price checks (`CHECK price > 0`), and stock quantities.
* **`orders`**: Customer order tracking, order status, and total order amounts.
* **`order_items`**: Line items linking orders to products with item-level prices and quantities.
* **`payments`**: Payment records, payment methods, and transaction amounts.
* **`product_reviews`**: Customer ratings (1–5 scale) and feedback timestamps.

---

## 🧹 2. Data Cleaning & Pipeline Fixes

* **Pre-Load Schema Hardening (DDL)**:
  * Expanded `customers.phone` to `VARCHAR(30)` to accept formatting symbols, spaces, and extensions without truncation.
  * Changed `products.added_on` and `product_reviews.review_date` to `DATETIME` to eliminate timestamp parsing errors.
* **Post-Load Query Cleaning (DQL)**:
  * Formatted phone numbers and names dynamically using `REGEXP_REPLACE()` and `CONCAT()`.
  * Audited missing values and orphaned records using `IS NULL` filters.

---

## 📊 3. Analytical Scope (42 Tasks / 6 Levels)

* **Level 1 — Basics (10 Tasks)**: Data projection, range filtering (`BETWEEN`), wildcard pattern matching (`LIKE 'A%'`), and multi-column sorting (`ORDER BY`).
* **Level 2 — Filtering & Formatting (6 Tasks)**: Line-item revenue calculations (`quantity * item_price`), date extraction (`DATE()`), and identifying stockouts (`stock_quantity = 0`).
* **Level 3 — Aggregations & GROUP BY (10 Tasks)**: Store KPIs (`COUNT`, `SUM`, `AVG`), customer spend totals, units sold per category, and daily order volumes.
* **Level 4 — Multi-Table JOINs (7 Tasks)**: Cross-table reporting combining orders, customers, and payments using `INNER JOIN`, `LEFT JOIN` (churn/unsold inventory checks), and `RIGHT JOIN`.
* **Level 5 — Subqueries (7 Tasks)**: Dynamic evaluations including products priced above store average, churn detection (`NOT IN`), and correlated subqueries for above-average customer orders.
* **Level 6 — Set Operations (2 Tasks)**: Customer engagement segmentation using `UNION` (placed orders OR reviewed products) and simulated `INTERSECT` (placed orders AND reviewed products).

---

## 🚀 4. How to Run

1. Open **MySQL Workbench 8.0 CE**.
2. Execute the **DDL** script to create the schema and tables.
3. Execute the **DML** script to ingest the dataset.
4. Run the queries sequentially from **Level 1 to Level 6** to view business reports.
