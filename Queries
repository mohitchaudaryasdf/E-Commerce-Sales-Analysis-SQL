USE ecommerce_sales;
USE ecommerce_sales;

-- 1. Total Customers
SELECT COUNT(*) AS total_customers
FROM customers;

-- 2. Total Products
SELECT COUNT(*) AS total_products
FROM products;

-- 3. Total Orders
SELECT COUNT(*) AS total_orders
FROM orders;

-- 4. Total Order Items
SELECT COUNT(*) AS total_order_items
FROM order_items;

-- 5. Total Revenue
SELECT
ROUND(SUM(quantity * selling_price),2) AS total_revenue
FROM order_items;

-- 6. Average Order Value
SELECT
ROUND(AVG(order_total),2) AS average_order_value
FROM
(
    SELECT
        order_id,
        SUM(quantity * selling_price) AS order_total
    FROM order_items
    GROUP BY order_id
) AS order_summary;

-- 7. Highest Order Value
SELECT
order_id,
ROUND(SUM(quantity * selling_price),2) AS order_value
FROM order_items
GROUP BY order_id
ORDER BY order_value DESC
LIMIT 1;

-- 8. Lowest Order Value
SELECT
order_id,
ROUND(SUM(quantity * selling_price),2) AS order_value
FROM order_items
GROUP BY order_id
ORDER BY order_value ASC
LIMIT 1;

-- 9. Average Product Price
SELECT
ROUND(AVG(price),2) AS average_product_price
FROM products;

-- 10. Total Quantity Sold
SELECT
SUM(quantity) AS total_quantity_sold
FROM order_items;

-- 11. Most Expensive Product
SELECT *
FROM products
ORDER BY price DESC
LIMIT 1;

-- 12. Cheapest Product
SELECT *
FROM products
ORDER BY price ASC
LIMIT 1;

-- 13. Total Stock Available
SELECT
SUM(stock) AS total_stock
FROM products;

-- 14. Average Quantity Per Order
SELECT
ROUND(AVG(quantity),2) AS average_quantity
FROM order_items;

-- 15. Number of Distinct Products Sold
SELECT
COUNT(DISTINCT product_id) AS unique_products_sold
FROM order_items;
-- 16. Total Male Customers
SELECT gender, COUNT(*) AS total_customers
FROM customers
GROUP BY gender;

-- 17. Customers State Wise
SELECT state, COUNT(*) AS total_customers
FROM customers
GROUP BY state
ORDER BY total_customers DESC;

-- 18. Customers City Wise
SELECT city, COUNT(*) AS total_customers
FROM customers
GROUP BY city
ORDER BY total_customers DESC;

-- 19. Top 10 Customers by Number of Orders
SELECT
c.customer_id,
CONCAT(c.first_name,' ',c.last_name) AS customer_name,
COUNT(o.order_id) AS total_orders
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.customer_id, customer_name
ORDER BY total_orders DESC
LIMIT 10;

-- 20. Top 10 Customers by Revenue
SELECT
c.customer_id,
CONCAT(c.first_name,' ',c.last_name) AS customer_name,
ROUND(SUM(oi.quantity * oi.selling_price),2) AS revenue
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id
JOIN order_items oi
ON o.order_id = oi.order_id
GROUP BY c.customer_id, customer_name
ORDER BY revenue DESC
LIMIT 10;

-- 21. Average Revenue Per Customer
SELECT
ROUND(SUM(oi.quantity * oi.selling_price) /
COUNT(DISTINCT c.customer_id),2) AS avg_revenue_per_customer
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id
JOIN order_items oi
ON o.order_id = oi.order_id;

-- 22. Customers Who Never Ordered
SELECT
c.customer_id,
CONCAT(c.first_name,' ',c.last_name) AS customer_name
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;

-- 23. Repeat Customers (More Than One Order)
SELECT
c.customer_id,
CONCAT(c.first_name,' ',c.last_name) AS customer_name,
COUNT(o.order_id) AS total_orders
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.customer_id, customer_name
HAVING COUNT(o.order_id) > 1
ORDER BY total_orders DESC;

-- 24. New Customers Per Year
SELECT
YEAR(join_date) AS year_joined,
COUNT(*) AS new_customers
FROM customers
GROUP BY YEAR(join_date)
ORDER BY year_joined;

-- 25. Customers Joined Per Month
SELECT
MONTHNAME(join_date) AS month_name,
COUNT(*) AS total_customers
FROM customers
GROUP BY MONTH(join_date), MONTHNAME(join_date)
ORDER BY MONTH(join_date);


-- 26. Top 10 Selling Products
SELECT
p.product_id,
p.product_name,
SUM(oi.quantity) AS total_quantity_sold
FROM products p
JOIN order_items oi
ON p.product_id = oi.product_id
GROUP BY p.product_id, p.product_name
ORDER BY total_quantity_sold DESC
LIMIT 10;

-- 27. Bottom 10 Selling Products
SELECT
p.product_id,
p.product_name,
SUM(oi.quantity) AS total_quantity_sold
FROM products p
JOIN order_items oi
ON p.product_id = oi.product_id
GROUP BY p.product_id, p.product_name
ORDER BY total_quantity_sold
LIMIT 10;

-- 28. Top 10 Products by Revenue
SELECT
p.product_id,
p.product_name,
ROUND(SUM(oi.quantity * oi.selling_price),2) AS revenue
FROM products p
JOIN order_items oi
ON p.product_id = oi.product_id
GROUP BY p.product_id, p.product_name
ORDER BY revenue DESC
LIMIT 10;

-- 29. Average Selling Price of Products
SELECT
ROUND(AVG(selling_price),2) AS average_selling_price
FROM order_items;

-- 30. Most Expensive Product
SELECT *
FROM products
ORDER BY price DESC
LIMIT 1;

-- 31. Cheapest Product
SELECT *
FROM products
ORDER BY price
LIMIT 1;

-- 32. Products Never Sold
SELECT
p.product_id,
p.product_name
FROM products p
LEFT JOIN order_items oi
ON p.product_id = oi.product_id
WHERE oi.product_id IS NULL;

-- 33. Revenue Generated by Each Product
SELECT
p.product_name,
ROUND(SUM(oi.quantity * oi.selling_price),2) AS revenue
FROM products p
JOIN order_items oi
ON p.product_id = oi.product_id
GROUP BY p.product_name
ORDER BY revenue DESC;

-- 34. Average Quantity Sold Per Product
SELECT
p.product_name,
ROUND(AVG(oi.quantity),2) AS average_quantity
FROM products p
JOIN order_items oi
ON p.product_id = oi.product_id
GROUP BY p.product_name
ORDER BY average_quantity DESC;

-- 35. Total Stock Available
SELECT
SUM(stock) AS total_stock
FROM products;

-- 36. Highest Stock Product
SELECT *
FROM products
ORDER BY stock DESC
LIMIT 1;

-- 37. Lowest Stock Product
SELECT *
FROM products
ORDER BY stock
LIMIT 1;

-- 38. Number of Products Sold
SELECT
COUNT(DISTINCT product_id) AS products_sold
FROM order_items;

-- 39. Total Quantity Sold Product Wise
SELECT
p.product_name,
SUM(oi.quantity) AS quantity_sold
FROM products p
JOIN order_items oi
ON p.product_id = oi.product_id
GROUP BY p.product_name
ORDER BY quantity_sold DESC;

-- 40. Product Sales Ranking
SELECT
p.product_name,
ROUND(SUM(oi.quantity * oi.selling_price),2) AS revenue
FROM products p
JOIN order_items oi
ON p.product_id = oi.product_id
GROUP BY p.product_name
ORDER BY revenue DESC;



-- 41. Monthly Revenue
SELECT
MONTHNAME(o.order_date) AS month_name,
ROUND(SUM(oi.quantity * oi.selling_price),2) AS revenue
FROM orders o
JOIN order_items oi
ON o.order_id = oi.order_id
GROUP BY MONTH(o.order_date), MONTHNAME(o.order_date)
ORDER BY MONTH(o.order_date);

-- 42. Yearly Revenue
SELECT
YEAR(o.order_date) AS year,
ROUND(SUM(oi.quantity * oi.selling_price),2) AS revenue
FROM orders o
JOIN order_items oi
ON o.order_id = oi.order_id
GROUP BY YEAR(o.order_date);

-- 43. Revenue by Order Status
SELECT
o.order_status,
ROUND(SUM(oi.quantity * oi.selling_price),2) AS revenue
FROM orders o
JOIN order_items oi
ON o.order_id = oi.order_id
GROUP BY o.order_status;
-- 44. Rank Products by Revenue
SELECT
p.product_name,
ROUND(SUM(oi.quantity * oi.selling_price),2) AS revenue,
RANK() OVER(
ORDER BY SUM(oi.quantity * oi.selling_price) DESC
) AS product_rank
FROM products p
JOIN order_items oi
ON p.product_id = oi.product_id
GROUP BY p.product_name;
-- 45 Row Number
SELECT
product_name,
price,
ROW_NUMBER() OVER(
ORDER BY price DESC
) AS row_num
FROM products;

-- 46. Running Revenue
SELECT
o.order_date,
SUM(oi.quantity*oi.selling_price) AS revenue,
SUM(SUM(oi.quantity*oi.selling_price))
OVER(ORDER BY o.order_date) AS running_revenue
FROM orders o
JOIN order_items oi
ON o.order_id=oi.order_id
GROUP BY o.order_date;

-- 47. Customers Spending Above Average
SELECT
customer_id,
total_spent
FROM
(
SELECT
o.customer_id,
SUM(oi.quantity*oi.selling_price) AS total_spent
FROM orders o
JOIN order_items oi
ON o.order_id=oi.order_id
GROUP BY o.customer_id
)t
WHERE total_spent >
(
SELECT AVG(total_amount)
FROM
(
SELECT
SUM(oi.quantity*oi.selling_price) AS total_amount
FROM orders o
JOIN order_items oi
ON o.order_id=oi.order_id
GROUP BY o.customer_id
)x
);

-- 48. View for Sales Report
CREATE VIEW sales_report AS
SELECT
o.order_id,
o.order_date,
p.product_name,
oi.quantity,
oi.selling_price,
oi.quantity*oi.selling_price AS revenue
FROM orders o
JOIN order_items oi
ON o.order_id=oi.order_id
JOIN products p
ON oi.product_id=p.product_id;



-- 49. Top Revenue Day
SELECT
o.order_date,
ROUND(SUM(oi.quantity*oi.selling_price),2) AS revenue
FROM orders o
JOIN order_items oi
ON o.order_id=oi.order_id
GROUP BY o.order_date
ORDER BY revenue DESC
LIMIT 1;

-- 50. Average Revenue Per Day
SELECT
ROUND(AVG(daily_revenue),2)
FROM
(
SELECT
SUM(quantity*selling_price) AS daily_revenue
FROM orders o
JOIN order_items oi
ON o.order_id=oi.order_id
GROUP BY o.order_date
);

