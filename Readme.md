# DBOps-project

### Create database
```CREATE DATABASE store;```

### Create user for migrations and tests<br>
```CREATE USER <user> WITH PASSWORD '<your password>';```<br>
```GRANT ALL PRIVILEGES ON DATABASE store TO <user>;```<br>
```GRANT ALL PRIVILEGES ON SCHEMA public TO <user>;```<br>
```GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO <user>;```
```ALTER DATABASE store OWNER TO <user>;```

### SELECT query
```
SELECT orders.date_created, SUM(order_product.quantity) as cnt
FROM orders
JOIN order_product ON orders.id = order_product.order_id
WHERE orders.status = 'shipped' AND orders.date_created > NOW() - INTERVAL '1 WEEK'
GROUP BY orders.date_created
ORDER BY orders.date_created desc;
```