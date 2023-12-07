# SQL-Stored-Procedures
Learn about SQL Stored Procedures with the help of examples. Learn how to create and use SQL stored procedures to reuse your code and improve the performance of your database.

In SQL, a stored procedure is a set of statement(s) that perform some defined actions. We make stored procedures so that we can reuse statements that are used frequently.
Stored procedures are thus similar to functions in programming. They can perform specified operations when we call them.

## Creating a Procedure

Create stored procedures using the CREATE PROCEDURE command followed by SQL commands. For example,
```sql
-- SQL Server

CREATE PROCEDURE us_customers AS
SELECT customer_id, first_name
FROM Customers
WHERE Country = 'USA';

```
```sql
-- PostgreSQL

CREATE PROCEDURE us_customers ()
LANGUAGE SQL
AS $$
SELECT customer_id, first_name
FROM Customers
WHERE Country = 'USA';
$$;
```
```sql
-- MySQL

DELIMITER //
CREATE PROCEDURE us_customers ()
BEGIN
SELECT customer_id, first_name
FROM Customers
WHERE Country = 'USA';
END //
DELIMITER ;
```
```sql
-- Oracle

CREATE PROCEDURE us_customers
AS res SYS_REFCURSOR;  
BEGIN
open res for
SELECT customer_id, first_name
FROM Customers
WHERE country = 'USA';
DBMS_SQL.RETURN_RESULT(res);
END;
```
The commands above create a stored procedure named us_customers in various DBMS. This procedure selects the customer_id and first_name columns of those customers who live in the USA from the Customers table.


