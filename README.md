# 🧾 Basic Sales Summary using SQLite, Python, and Matplotlib

This project demonstrates how to use **SQL within Python** to query sales data from a tiny SQLite database and visualize it using **matplotlib**.

## 📁 Files Included

- `sales_data.db`: SQLite database containing sample sales transactions
- `sales_summary.py` / `sales_summary.ipynb`: Python script or Jupyter Notebook to run SQL queries and generate visualizations
- `sales_chart.png`: Bar chart showing revenue by product

## 🚀 Features

- Connects to a SQLite database using `sqlite3`
- Runs basic SQL queries to:
  - Summarize total quantity and revenue per product
  - Identify the best-selling product by quantity
  - Show revenue per individual transaction
- Loads SQL output into a `pandas` DataFrame
- Visualizes revenue by product using a simple bar chart (`matplotlib`)

## 🧪 SQL Queries Used

```sql
-- 1. Total quantity & revenue per product
SELECT product, SUM(quantity) AS total_qty, SUM(quantity * price) AS revenue
FROM sales
GROUP BY product;

-- 2. Best-selling product by quantity
SELECT product, SUM(quantity) AS total_quantity
FROM sales
GROUP BY product
ORDER BY total_quantity DESC
LIMIT 1;

-- 3. Revenue per transaction
SELECT id, product, quantity, price, quantity * price AS transaction_revenue
FROM sales
ORDER BY transaction_revenue DESC;

📊 SALES SUMMARY REPORT
  product    total_qty    revenue
  Product A     13         260.00
  Product B     7          350.00
  Product C     11         165.00

🏆 BEST-SELLING PRODUCT
Product: Product A
Total Quantity Sold: 13
