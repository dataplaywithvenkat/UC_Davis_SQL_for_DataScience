# UC Davis SQL for Data Science Specilization
Repository for my course for the course [UC Davis Learn SQL Basics for Data Science Specialization](https://www.coursera.org/specializations/learn-sql-basics-data-science)

## Retrieveing Data with select Statement
Need to specify two pieces of Information to use a select Statement: what you want and where you want to select it from.

```SQL
SELECT prod_name
FROM Products;
```

Add multiple column names, be sure to use a comma

```SQL
SELECT prod_name,prod_id, prod_price
FROM Products;
```
(OR)

```SQL
SELECT prod_name,
        prod_id,
        prod_price
FROM Products;
```
Request all coulumns by using the asterisk(*) wildcard character insted of column names

```SQL
SELECT *
FROM Products;
```

IF your database is large - You might only want to see a sample of the Data

```SQL
SELECT columns you wish to see
FROM specific table
LIMIT number of records
```




