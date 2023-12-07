# SQL Stored Procedures

Learn about SQL Stored Procedures with the help of examples. Discover how to create and use SQL stored procedures to reuse your code and improve the performance of your database.

In SQL, a stored procedure is a set of statement(s) that perform some defined actions. Stored procedures are similar to functions in programming, allowing the reuse of frequently used statements.

## Creating a Procedure

Create stored procedures using the `CREATE PROCEDURE` command followed by SQL commands. For example:

### SQL Server

```sql
CREATE PROCEDURE us_customers AS
SELECT customer_id, first_name
FROM Customers
WHERE Country = 'USA';
```

### PostgreSQL

```sql
CREATE PROCEDURE us_customers ()
LANGUAGE SQL
AS $$
SELECT customer_id, first_name
FROM Customers
WHERE Country = 'USA';
$$;
```
