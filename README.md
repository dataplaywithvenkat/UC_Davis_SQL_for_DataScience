# UC Davis SQL for Data Science Specilization
Repository for my course for the course [UC Davis Learn SQL Basics for Data Science Specialization](https://www.coursera.org/specializations/learn-sql-basics-data-science)

# Part-1 : Getting Started and Selecting & Retrieving Data with SQL

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

## SQL Overview

[What is SQL and How is it Used?](https://aws.amazon.com/what-is/sql/)

[NTC Hosting: Structured Query Language (it's worth exploring this site, not just this singular posting)](https://www.ntchosting.com/encyclopedia/databases/structured-query-language/)

[SQLite Tutorial](https://www.w3resource.com/sqlite/)

## Data Modeling and ER Diagrams

[Norwalk Aberdeen: Entity-Relationship Diagrams (9 Minute YouTube Video)](https://www.youtube.com/watch?v=c0_9Y8QAstg)

[Star Schema vs. Snowflake Schema](https://vertabelo.com/blog/data-warehouse-modeling-star-schema-vs-snowflake-schema/)

[What is STAR Schema? (7 Minute YouTube Video)](https://www.youtube.com/watch?v=hQvCOBv_-LE)

[Data Modeling 101](http://www.agiledata.org/essays/dataModeling101.html)

[What is Data Modeling - An Introduction for Business Analysts](http://business-analysis-excellence.com/what-is-data-modeling/)

[Wikipedia: Data Modeling](https://en.wikipedia.org/wiki/Data_modeling)

## Comparing NoSQL and SQL

[SQL vs. NoSQL: 5 Critical Differences](https://www.integrate.io/blog/the-sql-vs-nosql-difference/#:~:text=SQL%20databases%20are%20vertically%20scalable,data%20like%20documents%20or%20JSON.)

[SQL vs. NoSQL: The Differences Explained + When to Use Each](https://www.coursera.org/articles/nosql-vs-sql)

[NoSQL vs. SQL Databases](https://www.coursera.org/articles/nosql-vs-sql)

# Part-2 : Filtering, Sorting, and Calculating Data with SQL

## Basics of Filtering with SQL

**Why Filter?**
- Be specific about the data you want to retrieve
- Reduce the number of records you retrieve
- Increase query performance
- Reduce the strain on the client application
- Governance Limitations

**WHERE Clause Operators**

```SQL
SELECT column_name, column_name
FROM table_name
WHERE column_name operator value;
```

| **Operator** | **Description**                                                                                       |
|--------------|-------------------------------------------------------------------------------------------------------|
| `=`          | Equal to. Used to specify a condition where the column value must be exactly equal to a given value.  |
| `!=` or `<>` | Not equal to. Used to specify a condition where the column value must not be equal to a given value.  |
| `>`          | Greater than. Used to specify a condition where the column value must be greater than a given value.  |
| `<`          | Less than. Used to specify a condition where the column value must be less than a given value.        |
| `>=`         | Greater than or equal to. Used to specify a condition where the column value must be greater than or equal to a given value. |
| `<=`         | Less than or equal to. Used to specify a condition where the column value must be less than or equal to a given value. |
| `BETWEEN`    | Used to specify a range to filter the column values.                                                  |
| `LIKE`       | Used to search for a specified pattern in a column. Often used with wildcard characters `%` and `_`.  |
| `IN`         | Used to specify multiple possible values for a column.                                                |
| `NOT IN`     | Used to exclude multiple possible values for a column.                                                |
| `IS NULL`    | Used to find rows where the column value is `NULL`.                                                   |
| `IS NOT NULL`| Used to find rows where the column value is not `NULL`.                                               |
| `AND`        | Used to combine multiple conditions in a `WHERE` clause. All conditions must be true.                 |
| `OR`         | Used to combine multiple conditions in a `WHERE` clause. At least one condition must be true.         |
| `NOT`        | Used to negate a condition.                                                                           |
| `EXISTS`     | Used to check if a subquery returns any rows.                                                         |
| `ANY`        | Used to compare a value to any value in a list or subquery.                                           |
| `ALL`        | Used to compare a value to all values in a list or subquery.                                          |

**Filtering on a Single condition**
```SQL
SELECT ProductName
,UnitPrice
,SupplierID
FROM Products
WHERE ProductName = 'Tofu';
```

```SQL
SELECT ProductName
,UnitPrice
,SupplierID
FROM Products
WHERE UnitPrice >= 75;
```

**Checking for Non-matches**
```SQL
SELECT ProductName
,UnitPrice
,SupplierID
FROM Products
WHERE ProductName <> 'Alice Mutton';
```

**Filtering with a Range of Values**

```SQL
SELECT ProductName
,UnitPrice
,SupplierID
,UnitsInStock
FROM Products
WHERE UnitsInStock BETWEEN 15 AND 80;
```

**Filtering No Value**

```SQL
SELECT ProductName
,UnitPrice
,SupplierID
,UnitsInStock
FROM Products
WHERE ProductName IS NULL;
```

## Advanced Filtering: IN, OR, and NOT

**IN Operator**
- Specifies a range of conditions
- Comma delimited list of values
- Enclosed in ()

```SQL
SELECT ProductName
,UnitPrice
,SupplierID
FROM Products
WHERE SupplierID IN (9,10,11);
```

**OR Operator**

- DBMS will not evaluate the second conditions in a WHERE clause if the first condition is met
- Use for any rows matching the specific condition

```SQL
SELECT ProductName
,ProductID
,UnitPrice
,SupplierID
,ProductName
FROM Products
WHERE ProductName = 'Tofu' OR 'Konbu';
```

**IN VS OR**
In works the same as OR

Benefits of IN
- Long list of Options
- IN executes faster than OR
- Don't have to think about the order with IN
- Can contain another SELECT

**OR with AND**

```SQL
SELECT ProductName
,UnitPrice
,SupplierID
FROM Products
WHERE SupplierID = 9 OR SupplierID = 11 AND UnitPrice > 15;
```

```SQL
SELECT ProductName
,UnitPrice
,SupplierID
FROM Products
WHERE (SupplierID = 9 OR SupplierID = 11) AND UnitPrice > 15;
```

**Order of Operations**
Can contain AND and OR operators
- SQL processes AND before OR
Use ()

**NOT Operator**

```SQL
SELECT *
FROM Employees
WHERE NOT City='London' AND NOT City ='Seattle';
```

## Using Wildcards in SQL

**What are Wildcards?**

- Special character used to match parts of a value
- Search pattern made from literal text, wildcard character, or a combination
- Uses LIKE as an Operator
- Can only be used with strings
- Cannot be used for non-text datatypes
- Helpful for data scientists as they explore string variables

**Using % Wildcards**

Wildcard | Action
`%Pizza` | Grabs anything ending with the word Pizza
`Pizza%` | Grabs anything after the word Pizza
`%Pizza%` | Grabs anything before and after the word Pizza

## Sorting with ORDER BY
## Math Operations
## Aggregate Functions
## Grouping Data with SQL
## Putting it All Together
## Module 2 Practice Quiz
## SQL for Various Data Science Languages














