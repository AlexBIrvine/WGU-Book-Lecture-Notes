---
Date: 2020/2/18
---

# Module 8 - Displaying Data from Multiple Tables

## 8.1 - Describe the Different Types of Joins and Their Features

There are two main ways that JOIN is categorized: Inner vs. Outer / Equijoin vs Non-Equijoin.  
These two categories are separate, not mutually exclusive.

<u>**Inner vs Outer**</u>:

- Inner joins connect rows on two or more tables if there are matched rows on all tables being joined.
- Outer joins connect rows on two or more tables if there exists data in at least one table. Unmatched rows will still be included.

<u>**Equijoin vs Non-Equijoin**</u>:

- Equijoins look for an exact match of data.
- Non-equijoins look for inequalities (less than or greater than relationships).

<u>**Cartesian Join**</u>: Joins every row of one table to every row of another table.  
Also known as a **CROSS JOIN**. This does NOT let you specify a join clause (unlike every other type of join) but does allow a WHERE clause.

---

## 8.2 - Use SELECT Statements to Access Data from More Than One Table Using Equijoins and Non-Equijoins

Author note:  
Too many tables being joined together causes performance issues, but what is too many?  
General rule of thumb is that 5 is too many, but if it makes good sense to join more, then join more.

### Inner Joins

Returns a merged row from two or more tables if and only if there are matched values among all joined tables.  
<u>**Note**</u>: The word `INNER` is not required, but good practice for readability.

<center>Example:</center>

```
PORTS TABLE                             |  SHIPS TABLE
                                        |
PORT_ID                PORT_NAME        |  SHIP_ID                SHIP_NAME            HOME_PORT_ID
---------------------- ---------------  |  ---------------------- -------------------- -------------------
1                      Baltimore        |  1                      Codd Crystal         1
2                      Charleston       |  2                      Codd Elegance        3
3                      Tampa            |  3                      Codd Champion
4                      Miami            |  4                      Codd Victorious      3
                                        |  5                      Codd Grandeur        2
                                        |  6                      Codd Prince          2
```

<center>Simple Inner Join</center>

```SQL
SELECT   SHIP_ID, SHIP_NAME, PORT_NAME
FROM     SHIPS INNER JOIN PORTS
ON       HOME_PORT_ID = PORT_ID
ORDER BY SHIP_ID;
```

<center>With WHERE clause</center>

```SQL
SELECT   SHIP_ID, SHIP_NAME, PORT_NAME
FROM     SHIPS INNER JOIN PORTS
ON       HOME_PORT_ID = PORT_ID
WHERE    PORT_NAME = 'Charleston'
ORDER BY SHIP_ID;
```

<u>**Old vs New syntax**</u>: Old syntax (the one you originally learned even) uses `WHERE` instead of `ON`.  
So `SELECT... FROM... WHERE... AND...` instead of `SELECT... FROM... ON... WHERE...`.  
Old syntax didn't also use teh word `JOIN`, so it just listed the tables in the `FROM` section.

Use aliases to distinguish between tables with the same column names.

<center>Alias example</center>

```SQL
SELECT   EM.EMPLOYEE_ID, LAST_NAME, STREET_ADDRESS
FROM     EMPLOYEES EM INNER JOIN ADDRESSES AD
ON       EM.EMPLOYEE_ID = AD.EMPLOYEE_ID;
```

### Natural Joins

Natural Joins tells SQL to locate any columns in the two tables iwth a common name, and use them to join the tables.

<center>Example</center>

```SQL
SELECT   EMPLOYEE_ID, LAST_NAME, STREET_ADDRESS
FROM     EMPLOYEES NATURAL LEFT JOIN ADDRESSES;
```

Notice the lack of `ON` keyword in the above example.

### USING

The `USING` keyword acts like an explicit Natural Join.  
Here is the above Natural Join example with USING:

```SQL
SELECT   EMPLOYEE_ID, LAST_NAME, STREET_ADDRESS
FROM     EMPLOYEES LEFT JOIN ADDRESSES
         USING (EMPLOYEE_ID);
```

### Multi-Table Joins

Example of three table join:

```SQL
1.  SELECT  P.PORT_NAME, S.SHIP_NAME, SC.ROOM_NUMBER
2.  FROM    PORTS P JOIN SHIPS S ON P.PORT_ID = S.HOME_PORT_ID
3.                  JOIN SHIP_CABINS SC ON S.SHIP_ID = SC.SHIP_ID;
```

<u>**Notice**</u>:

- FROM keyword only appears once.
- Line 3 opens with a JOIN keyword, joining the result of line 2 to the SHIP_CABINS table.

### Non-Equijoins

Non-Equijoins use inequalities to compare the rows of two or more tables.

```SQL
SELECT S.SCORE_ID, S.TEST_SCORE, G.GRADE
FROM   SCORES S JOIN GRADING G
ON     S.TEST_SCORE BETWEEN G.SCORE_MIN AND G.SCORE_MAX;
```

---

## 8.3 - Join a Table to Itself by Using a Self-Join

Writing a query that joins a table to itself. (Useful when trying to link data by attributes)

---

## 8.4 - View Data That Generally Does Not Meet a Join Condition by Using Outer Joins

Outer joins can include NULL data.
