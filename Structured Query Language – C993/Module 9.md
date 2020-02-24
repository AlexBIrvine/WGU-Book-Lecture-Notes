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

Example:

<u>**Task**</u>: Our task is to go back to our historical invoices and give a 10 percent discount to whomever placed our single biggest order for their respective quarter.  
So in the first quarter, we need to find the single biggest invoice and determine a 10 percent discount on that invoice, then do the same thing for the second quarter, and so on.

<u>**Steps**</u>:

1. ID the row with the highest value for TOTAL_PRICE for any given quarter.
   - To do this we'll use `TO_CHAR` format `mask Q` on the ORDER_DATE column.
2. Update an invoice only if it has the hightest TOTAL_PRICE for the quarter.

<center>Example SQL</center>

```SQL
UPDATE INVOICES INV
SET TERMS_OF_DISCOUNT = '10 PCT'
WHERE TOTAL_PRICE = (SELECT MAX(TOTAL_PRICE)
                     FROM   INVOICES
                     WHERE  TO_CHAR(INVOICE_DATE, 'RRRR-Q') =
                            TO_CHAR(INV.INVOICE_DATE, 'RRRR-Q'));
```

---

## 9.6 - Use the EXISTS and NOT EXISTS Operators

<u>**EXISTS**</u>: Tests if any rows in a subquery exists, returns true if so.

This following example looks for PORTS that have any sort of record at all in the SHIPS table with a HOME_PORT_ID value that matches any of the PORT_ID values.

```SQL
SELECT PORT_ID, PORT_NAME
FROM   PORTS P1
WHERE  EXISTS (SELECT *
               FROM   SHIPS S1
               WHERE  P1.PORT_ID = S1.HOME_PORT_ID);
```

This type of query is sometimes referred to as a `semijoin`.

---

## 9.7 - Use the WITH Clause

<u>**WITH**</u>: Allows you to assign a name to a subquery block, allowing you to reference the nbame from elsewhere in the query.

<center>Example of WITH</center>

```SQL
WITH
PORT_BOOKINGS AS (
    SELECT P.PORT_ID, P.PORT_NAME, COUNT(S.SHIP_ID) CT
    FROM   PORTS P, SHIPS S
    WHERE  P.PORT_ID  = S.HOME_PORT_ID
    GROUP BY P.PORT_ID, P.PORT_NAME
),
DENSEST_PORT  AS (
    SELECT MAX(CT) MAX_CT
    FROM   PORT_BOOKINGS
)
SELECT PORT_NAME
FROM   PORT_BOOKINGS
WHERE  CT = (SELECT MAX_CT FROM DENSEST_PORT);
```

---

## 9.8 - Write Single-Row and Multiple-Row Subqueries

### Single-Row Subqueries

You can run into issues with subqueries when the answer is dependant on only getting 1 (and only 1) result.
To accomplish this, you can get very specific with multiple subqueries inside a subquery.
