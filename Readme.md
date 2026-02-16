# DBOps-project

### Create database
```CREATE DATABASE store;```

### Create user for migrations and tests<br>
```CREATE USER store_user WITH PASSWORD 'password';```<br>
```GRANT ALL PRIVILEGES ON DATABASE store TO store_user;```<br>
```GRANT ALL PRIVILEGES ON SCHEMA public TO store_user;```<br>
```GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO store_user;```

### SELECT query
```
SELECT o.date_created, SUM(op.quantity) as cnt
FROM orders o
JOIN order_product op ON o.id = op.order_id
WHERE o.status = 'shipped' AND o.date_created > NOW() - INTERVAL '7 DAY'
GROUP BY o.date_created
ORDER BY o.date_created desc;
```