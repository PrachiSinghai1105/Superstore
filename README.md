
# Following are the link to Tabaleau Visualizations.

https://public.tableau.com/app/profile/prachi.singhai/viz/TAbleauSuperstore/Story1?publish=yes

https://public.tableau.com/app/profile/prachi.singhai/viz/TableauSuperstoreCategoryandSubcategoryAnalysis/Story2?publish=yes

https://public.tableau.com/app/profile/prachi.singhai/viz/TableauSuperstoreCustomeranalysis/Story3?publish=yes

# INRODUCTION

This repository contains a series of SQL queries executed on the Superstore database. Each query explores different aspects of the data, providing insights into sales, profits, and customer behavior.

Query 1: Basic Data Retrieval
SELECT * FROM superstore LIMIT 5;
This query retrieves the first 5 rows from the 'superstore' table, offering a quick glance at the dataset.

Query 2: Total Sales and Profit per Year
SELECT
    year(OrderDate) AS year,
    SUM(sales) AS total_sales,
    SUM(profit) AS total_profit
FROM
    superstore
GROUP BY year
ORDER BY year ASC;

The query calculates the total sales and profits for each year in the dataset.

Query 3: Total Sales and Profit per Quarter

SELECT
    Year(OrderDate) AS year,
    CASE
        WHEN MONTH(OrderDate) IN (1,2,3) THEN 'Q1'
        WHEN MONTH(OrderDate) IN (4,5,6) THEN 'Q2'
        WHEN MONTH(OrderDate) IN (7,8,9) THEN 'Q3'
        ELSE 'Q4'
    END AS quarter,
    SUM(sales) AS total_sales,
    SUM(profit) AS total_profit
FROM superstore
GROUP BY year, quarter
ORDER BY year, quarter;

This query breaks down total sales and profits by quarter for each year.

Query 4: Total Sales and Profits by Region

SELECT
    region, SUM(sales) AS total_sales, SUM(profit) AS total_profits
FROM superstore
GROUP BY region
ORDER BY total_profits DESC;

The query explores the total sales and profits for each region.

Query 5: Profit Margin by Region

SELECT
    region, ROUND((SUM(profit) / SUM(sales)) * 100, 2) as profit_margin
FROM superstore
GROUP BY region
ORDER BY profit_margin DESC;


This query calculates the profit margin for each region.

