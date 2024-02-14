## 1
```sql
WITH orders_client AS (
	SELECT customer_id, (o.quantity * p.price) as sum_order FROM orders o
	JOIN products p ON p.product_id = o.product_id
	WHERE o.order_date > '2024-01-13'
	ORDER BY 1
)
SELECT p.first_name, p.last_name, SUM(sum_order) FROM orders_client
JOIN customers p ON p.customer_id = orders_client.customer_id
GROUP BY 1, 2
ORDER BY 3 DESC
```
![image](https://github.com/rusinadaria/sql/assets/112808317/e806103e-ef69-4847-95bc-6163258a95cd)


## 2
```sql
CREATE VIEW table AS
(SELECT customer_id, (o.quantity * p.price) as sum_order FROM orders o
JOIN products p ON p.product_id = o.product_id)

SELECT first_name, last_name FROM customers c
JOIN table ON c.customer_id = table.customer_id
```
![image](https://github.com/rusinadaria/sql/assets/112808317/b6ba9f2a-fb91-4fba-abee-b85554204408)


