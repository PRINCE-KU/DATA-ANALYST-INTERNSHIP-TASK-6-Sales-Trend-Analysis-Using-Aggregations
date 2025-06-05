# DATA-ANALYST-INTERNSHIP-TASK-6-Sales-Trend-Analysis-Using-Aggregations
📚 INTERVIEW QUESTIONS & ANSWERS
1. How do you group data by month and year in SQL?
📌 Answer:
Use the EXTRACT() function to get year and month from a date, and then use GROUP BY.
SELECT 
  EXTRACT(YEAR FROM order_date) AS year,
  EXTRACT(MONTH FROM order_date) AS month
FROM online_sales
GROUP BY year, month;
2. What's the difference between COUNT(*) and COUNT(DISTINCT col)?
📌 Answer:

Function	Meaning
COUNT(*)	Counts all rows including duplicates and NULLs
COUNT(DISTINCT column)	Counts only unique values in that column, ignores NULLs
COUNT(*)                  -- counts all rows  
COUNT(DISTINCT order_id)  -- counts unique orders
3. How do you calculate monthly revenue?
📌 Answer:
Use SUM(amount) grouped by month and year.
SELECT 
  EXTRACT(MONTH FROM order_date) AS month,
  SUM(amount) AS monthly_revenue
FROM online_sales
GROUP BY month;
4. What are aggregate functions in SQL?
📌 Answer:
Aggregate functions are used to perform calculations on groups of rows.

🛠 Common ones:

SUM() → Total

AVG() → Average

COUNT() → Count

MIN() → Minimum

MAX() → Maximum

SELECT SUM(amount), COUNT(*) FROM online_sales;
5. How to handle NULLs in aggregates?


📌 Answer:
Most aggregate functions ignore NULL values by default (except COUNT(*)).
-- NULLs are ignored
SELECT AVG(amount), SUM(amount) FROM online_sales;
If you want to include/exclude explicitly, use COALESCE(amount, 0).


6. What’s the role of ORDER BY and GROUP BY?
📌 Answer:

Clause	Purpose
GROUP BY	Groups rows to apply aggregate functions
ORDER BY	Sorts result rows (ASC or DESC)
-- Group for aggregation
GROUP BY EXTRACT(MONTH FROM order_date)

-- Sort result
ORDER BY monthly_revenue DESC
-- Group for aggregation
GROUP BY EXTRACT(MONTH FROM order_date)

-- Sort result
ORDER BY monthly_revenue DESC
7. How do you get the top 3 months by sales?
📌 Answer:
Sort by revenue in descending order, then use LIMIT 3.
SELECT 
  EXTRACT(MONTH FROM order_date) AS month,
  SUM(amount) AS monthly_revenue
FROM online_sales
GROUP BY month
ORDER BY monthly_revenue DESC
LIMIT 3;

