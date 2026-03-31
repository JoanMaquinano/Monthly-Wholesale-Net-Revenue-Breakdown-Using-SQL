# Monthly Wholesale Net Revenue Analysis

## Overview
This project analyzes wholesale sales data to calculate monthly net revenue by
product line and warehouse. The goal is to provide stakeholders with insight into
which products and warehouses contribute the most net revenue over time.

## Business Question
How much net revenue did each product line generate per month per warehouse?

## Metric Definition
Net Revenue = Total Sales − Payment Fees

## Tools Used
- SQL
- pandas (via DataCamp DataLab)

## Query
```sql
SELECT
    product_line,
    TO_CHAR(order_date, 'Month') AS month,
    warehouse,
    SUM(total) - SUM(payment_fee) AS net_revenue
FROM sales
WHERE TO_CHAR(order_date, 'Month') IN ('June', 'July', 'August')
GROUP BY
    product_line,
    month,
    warehouse
ORDER BY
    product_line,
    month,
    net_revenue DESC;
