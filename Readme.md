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
SELECT o.date_created, SUM(op.quantity) as cnt
FROM orders o
JOIN order_product op ON o.id = op.order_id
WHERE o.status = 'shipped' AND o.date_created > NOW() - INTERVAL '1 WEEK'
GROUP BY o.date_created
ORDER BY o.date_created desc;
```