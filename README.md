# project-234
![image](https://github.com/manasvijain20/project-234/assets/74360258/b3d3b706-0d40-49c2-9e87-5a31f3d2df1e)

WITH query_1 AS
(SELECT
order_items.id as order_id,
customers.last_name as last_name,  
customers.phone as phone
FROM order_items LEFT JOIN company_orders
ON order_items.order_id = company_orders.id LEFT JOIN customers ON company_orders.customer_id = customers.id),

query_2 AS (
SELECT
order_items.id as order_id,
company_products.name as product_name, 
suppliers.contact_name as supplier_contact_name
FROM company_products LEFT JOIN suppliers 
ON suppliers.id = company_products.supplier_id
LEFT JOIN order_items
ON company_products.id = order_items.product_id)

SELECT query_1.last_name, query_1.phone, query_2.product_name, query_2.supplier_contact_name
FROM query_1 JOIN query_2 
ON query_1.order_id = query_2.order_id
