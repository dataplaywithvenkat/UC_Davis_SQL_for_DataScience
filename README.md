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

*LIMITING RESULTS USING DIFFERENT SYNTAXES*

*SQLITE*
```sql
SELECT prod_name
FROM Products
LIMIT 5;
```

*Oracle*
```sql
SELECT prod_name
FROM Products
WHERE ROWNUM <=5;
```

*db2*
```sql
SELECT prod_name
FROM Products
FETCH FIRST 5 ROWS ONLY;
```

## Creating Tables

**Creating Your Own Table**

```SQL
CREATE TABLE Shoes
(
Id Char(10) PRIMARY KEY,
Brand Char(10) NOT NULL,
Type Char(250) NOT NULL,
Color Char(250) NOT NULL,
Price decimal(8,2) NOT NULL,
Desc Varchar(750) NULL
)
```

**Nulls and Primary Keys**

- Every column is either NULL or NOT NULL
- An error will be returned if one tries to submit a column with no values
- Don't confuse null values with empty strings
- Primary keys can not be null

**Adding Data to the Table**

```SQL
INSERT INTO Shoes
VALUES("123456",
        'Gucci',
        'Slippers',
        'Pink',
        '695.00',
        NULL);
```

## Creating Temporary Tables

- The most crucial point to understand about temporary tables is that they are deleted when the current client session ends, which is why they are referred to as temporary tables.

**Why craeting temporary tables?**

- Faster than creating a real table
- Useful for complex queries using subsets and joins

**How to create temporary table**

```SQL
CREATE TEMPORARY TABLE Scandals AS
(
        SELECT *
        FROM shoes
        WHERE shoe_type = 'sandals'
)
```

## Adding Comments to SQL

- - Use this for single line comment
/* */ Use this for section comments

**SINGLE LINE**
```SQL
SELECT shoe_id
--,brand_id
,shoe_name
from shoes
```

**SECTION**
```SQL
SELECT shoe_id
/*,brand_id
,shoe_name
*/
from shoes
```

```SQL

```












