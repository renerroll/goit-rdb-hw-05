
# SQL Relation DB HW05

## 1. 

```sql
SELECT od.*, 
       (SELECT o.customer_id 
        FROM ORDERS_HW3.orders o 
        WHERE o.id = od.order_id) AS customer_id
FROM ORDERS_HW3.order_details od;
```

## 2. 
![SQL command5](2.png)

```sql
SELECT od.* 
FROM ORDERS_HW3.order_details od
WHERE od.order_id IN (SELECT o.id FROM ORDERS_HW3.orders o WHERE o.shipper_id = 3);

```

## 3. 
![SQL command5](3.png)

```sql
SELECT temp1.order_id, AVG(temp1.quantity) AS avg_quantity
FROM (
    SELECT * 
    FROM ORDERS_HW3.order_details 
    WHERE quantity > 10
) AS temp1
GROUP BY temp1.order_id;
```

## 4. 
![SQL command5](4.png)

```sql
SELECT @@version;

WITH temp AS (SELECT * FROM ORDERS_HW3.order_details WHERE quantity > 10)
SELECT order_id, AVG(quantity) FROM temp
GROUP BY order_id;
```


## 5. 
![SQL command5](5.png)

```sql
DROP FUNCTION IF EXISTS divide_float;
DELIMITER //

CREATE FUNCTION `divide_float` (num1 FLOAT, num2 FLOAT)
RETURNS FLOAT
NO SQL
DETERMINISTIC
```


