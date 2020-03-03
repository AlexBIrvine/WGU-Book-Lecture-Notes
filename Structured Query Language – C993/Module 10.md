---
Date: 2020/2/25
---

# Module 10 - Managing Schema Objects

## 10.1 - Describe How Schema Objects Work

<u>**Schema objects**</u>: Objects that are "owned" by a user and exist in a collection within the user account.

- Tables
- Views
- Indexes
- Sequences

<u>**Tables**</u>: Where all data in a database is stored. Information of the tables is stored in the `data dictionary`.  
<u>**Constraints**</u>: A rule on a table that restricts the values that can be added.  
<u>**Views**</u>: A "saved SELECT statement". It contains no data, just is the results of a previous SELECT.  
<u>**Indexes**</u>: ID's one or more columns that will be frequently used. Increases performance of frequently used searches.  
<u>**Sequences**</u>: A tracker of numbers, it knows what number it's on and what number comes next (used for Ids?).

---

## 10.2 - Create Simple and Complex Views with Visible/Invisible Columns

Once a view is created, you can refer to it in a SELECT statement as if it was a table.

<center>Example of creating a view of a larger Employees table in order to not show personal information:</center>

```SQL
CREATE VIEW VW_EMPLOYEES AS
       SELECT EMPLOYEE_ID, LAST_NAME, FIRST_NAME, PRIMARY_PHONE
       FROM EMPLOYEES;
```

<u>**Steps for creating views**</u>:

1. Use keyword `CREATE VIEW`.
2. Optional keyword `OR REPLACE` can be used.
3. Insert the name of the view.
4. Use the keyword `AS`.
5. Use a valid `SELECT` statement to get view.

You can't use an INSERT statement to a view since it won't hold the PK data.

You will be prevented from using `INSERT`, `UPDATE`, or `DELETE` if you create a view based on a `SELECT` statement that includes any of the following:

- Omission of any required columns (`NOT NULL`) in that underlying table
- `GROUP BY` or any other aggregation, such as set operators
- `DISTINCT`
- A `FROM` clause that references more than one table—that is, subqueries in the SELECT or most joins.

<u>**Inline Views**</u>: Views that are not named, but instead wrapped by (parentheses):

```SQL
SELECT A.SHIP_ID, A.COUNT_CABINS, B.COUNT_CRUISES
FROM (SELECT    SHIP_ID, COUNT(SHIP_CABIN_ID) COUNT_CABINS
      FROM      SHIP_CABINS
      GROUP BY  SHIP_ID) A

      JOIN

     (SELECT   SHIP_ID, COUNT(CRUISE_ORDER_ID) COUNT_CRUISES
      FROM     CRUISE_ORDERS
      GROUP BY SHIP_ID) B

ON    A.SHIP_ID = B.SHIP_ID;
```

A table can have an `INVISIBLE` column, which is created by using it's keyword.  
By using this feature, the column and data will exist but not show up in the `DESC` keyword.  
To `INSERT` data into an `INVISIBLE` column, you must name it in the `INSERT` keyword.

```SQL
CREATE TABLE SHIP_ADMIN
( SHIP_ADMIN_ID       NUMBER(7)     PRIMARY KEY
, SHIP_ID             NUMBER
, CONSTRUCTION_COST   NUMBER(14,2)  INVISIBLE
);
```

---

## 10.3 - Create, Maintain, and Use Sequences

<u>**Sequences**</u>: Predominantly used to generate data for primary key columns in tables.

<center>Creating a basic sequence</center>

```SQL
CREATE SEQUENCE SEQ_ORDER_ID;
```

A `sequence_option` can be added to the end of the above statement. Those options:  
<u>**INCREMENT BY**</u>: What to increment by. Default = 1.  
<u>**START WITH**</u>: Where to start in the sequence. Expects an integer.  
<u>**MAXVALUE**</u>: The max value that it can be. Default = NOMAXVALUE.  
<u>**NOMAXVALUE**</u>: Explicitly states there is no max value.  
<u>**MINVALUE**</u>: The minimum value, used in negative increment by sequences.  
<u>**NOMINVALUE**</u>: Explicitly states there is no min value.  
<u>**CYCLE**</u>: Specifies that when the sequence reaches it's max, to start again at the min.  
<u>**NOCYLCE**</u>: Explicitly states to not cycle.

You can use created sequences by using a `sequence_function`:  
<u>**NEXTVAL**</u>: Gets the next value.  
<u>**CURRVAL**</u>: Gets the current value.

---

## 10.4 - Create and Maintain Indexes Including Invisible Indexes and Multiple Indexes on the Same Columns
