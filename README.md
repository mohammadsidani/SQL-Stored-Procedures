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

### MySQL

```sql
DELIMITER //
CREATE PROCEDURE us_customers ()
BEGIN
    SELECT customer_id, first_name
    FROM Customers
    WHERE Country = 'USA';
END //
DELIMITER ;
```
### Oracle

```sql
CREATE PROCEDURE us_customers
AS res SYS_REFCURSOR;  
BEGIN
    OPEN res FOR
    SELECT customer_id, first_name
    FROM Customers
    WHERE country = 'USA';
    DBMS_SQL.RETURN_RESULT(res);
END;
```

The commands above create a stored procedure named us_customers in various DBMS. This procedure selects the **customer_id** and **first_name** columns of those customers who live in the USA from the **Customers table**.


## Executing Stored Procedure

Now, whenever we want to fetch all customers who live in the USA, we can simply call the procedure mentioned above. For example:

### SQL Server, Oracle

```sql
EXEC us_customers;
```

### PostgreSQL, MySQL

```sql
CALL us_customers();
```

## Drop Procedure

Stored procedures can be deleted using the DROP PROCEDURE command. For example:

### SQL Server, PostgreSQL, MySQL

```sql
DROP PROCEDURE us_customers;
```

Here, the SQL command deletes the `us_customers procedure` that we created previously.

![dbjpg](https://github.com/mohammadsidani/SQL-Stored-Procedures/assets/86320260/b49f554b-7d0d-4642-a870-06ec36a5e698)

