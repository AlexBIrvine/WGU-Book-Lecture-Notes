---
Date: 2020/2/24
---

# Module 9 - Using Subqueries to Solve Queries

## 9.1 - Define Subqueries

A subquery is a query that is embedded in another statement.  
They create view objects.

Statements that accept subqueries:

- SELECT
- INSERT
- UPDATE
- MERGE
- DELETE

---

## 9.2 - Describe the Types of Problems Subqueries Can Solve

The example the book gives is:

1. There is a table with sales reps, the year, and total sales of that year.
2. The user wants to know who sold higher than the average this year than the previous year.
3. The user makes a subquery to get the average sales for the previous year:

<center>Query to get previous years sales</center>

```SQL
SELECT AVG(TOTAL_SALES) AVG_SALES
FROM   SALES_DATA
WHERE  YEAR = 2019;
```

4. We can then add this query to another query to compare the current year to last year's average:

<center>Full problem</center>

```SQL
SELECT REP
FROM   SALES_DATA
WHERE  YEAR = 2020
AND    TOTAL_SALES > (SELECT AVG(TOTAL_SALES)
                      FROM   SALES_DATA
                      WHERE  YEAR = 2019);
```

---

## 9.3 - Describe the Types of Subqueries

<u>**Single-row subqueries**</u>: Returns a single row’s worth of data in its result.  
<u>**Multiple-row subqueries**</u>: Returns zero, one, or more rows in its result.  
<u>**Multiple-column subqueries**</u>: Returns a single column & may be either single-row / multiple-row.  
<u>**Correlated subqueries**</u>: Specifies columns that belong to tables that are also referenced by the parent query. In a multilevel series of subqueries, subqueries within subqueries, and so on.  
<u>**Scalar subqueries**</u>: Is a single-row subquery consists of only one column’s worth of output.

---

## 9.4 - Query Data Using Correlated Subqueries

A correlated subquery is a query that is integrated with a parent query.  
Correlated subqueries include references to elements of a parent query, and thus, they do not exist as stand-alone queries.

This example lists all the cabins in the ship whose size—as measured by the SQ_FT column—is larger than the average cabin for its ROOM_STYLE.

```SQL
SELECT   A.SHIP_CABIN_ID, A.ROOM_STYLE, A.ROOM_NUMBER, A.SQ_FT
FROM     SHIP_CABINS A
WHERE    A.SQ_FT > (SELECT AVG(SQ_FT)
                    FROM   SHIP_CABINS
                    WHERE  ROOM_STYLE = A.ROOM_STYLE)
ORDER BY A.ROOM_NUMBER;
```

---

## 9.5 - Update and Delete Rows Using Correlated Subqueries

### UPDATE with a correlated subquery

UPDATE statements can have a correlated subquery in the following places:

- SET clause
- WHERE clause

...
