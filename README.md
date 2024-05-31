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

## Advanced Filtering: IN, OR, and NOT
## Using Wildcards in SQL
## Sorting with ORDER BY
## Math Operations
## Aggregate Functions
## Grouping Data with SQL
## Putting it All Together
## Module 2 Practice Quiz
## SQL for Various Data Science Languages














