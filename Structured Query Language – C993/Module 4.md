---
Date: 2020/2/12
---

# Module 4 - Restricting and Sorting Data

## 4.1 - Sort the Rows That Are Retrieved by a Query

<u>**ORDER BY**</u>: Used to sort the rows that are retrieved by a SELECT statement. This is ONLY used by a SELECT statement, and no other statements.

<center>Simple example</center>

```SQL
SELECT   ADDRESS_ID, STREET_ADDRESS, CITY, STATE, COUNTRY
FROM     ADDRESSES
ORDER BY STATE, CITY;
```

Notes:

- The `NULL` value will show up last, as it's considered the "highest" value.
- You an add as many pararameters to ORDER BY as you like, and it will sort in that order.
- By default ORDER BY sorts in asennding (ASD) order (lowest to hightest), but adding DESC will sort it in descending order.
- You can use expressions to sort by (example below: `PROJECT_COST/PART_COST`).

<center>Descending order, mixed order, using expressions</center>

```SQL
SELECT   SHIP_ID, PROJECT_COST, PROJECT_NAME, PART_COST
FROM     PROJECTS
ORDER BY SHIP_ID ASC, PROJECT_COST/PART_COST DESC;
```

<u>**Alias**</u>: Using the `AS` statement or quotes next to a column name, you can create a temporary name to refer to it as.

<center>Using alias</center>

```SQL
SELECT   PROJECT_ID, PROJECT_NAME, PROJECT_COST, DATES, PROJECT_COST/DATES AS PER_DAY_COST
FROM     PROJECTS
ORDER BY PER_DAY_COST;

-- or

SELECT   PROJECT_ID, PROJECT_NAME, PROJECT_COST, DATES, PROJECT_COST/DATES "Cost Per Day"
FROM     PROJECTS
ORDER BY "Cost Per Day";
```

---

## 4.2 - Limit the Rows That Are Retrieved by a Query

<u>**WHERE**</u>: Limits the results of a SELECT, UPDATE, or DELETE statement.

<center>Simple example</center>

```SQL
SELECT EMPLOYEE_ID
FROM   WORK_HISTORY
WHERE  SHIP_ID = 3;
```

<u>**Full list of operators accepted by WHERE**</u>

```
=
>=
>
<
<=
!=
<>   (also not equal)
^=   (also not equal)
IN
LIKE (enables wildcard characters)
IS   (used with NULL and NOT NULL)
```

Note:

- In `LIKE`, the % symbol is the wild card character

(The rest of the chapter goes into boolean algebra, and using that with the `WHERE` statement. Most is review)

---

## 4.3 - Use Ampersand Substitution to Restrict and Sort Output at Run Time

Ampersand substitution is exclusive to SQL\*Plus and is not part of ANSI SQL.

<u>**Ampersand substitution**</u>: is a way to declare variables at runtime.

<center>Example program</center>

```SQL
1   SELECT   ROOM_NUMBER, STYLE, WINDOW
2   FROM     SHIP_CABINS
3   WHERE    ROOM_NUMBER = &RNO
4   ORDER BY ROOM_NUMBER;
```

<center>Program at runtime</center>

```SQL
Enter value for rno:  --user enters 104
old   3: WHERE    ROOM_NUMBER = &RNO
new   3: WHERE    ROOM_NUMBER = 104


ROOM  STYLE   WINDOW
----  -----   ------
104   Suite   None
```

(The book goes into more examples, but understanding the above should be enough)

---

## 4.4 - Use the SQL Row Limiting Clause

<u>**FETCH**</u>: Used to limit the number of rows returned not with business logic (like `WHERE` does) but by the number of rows.

<center>Simple example</center>

```SQL
SELECT * FROM ORDERS
FETCH FIRST 8 ROWS ONLY;

-- or

SELECT * FROM ORDERS
FETCH FIRST 50 PERCENT ROWS ONLY;
```

Note:

- `FIRST` or `NEXT` keyword must follow `FETCH`.
-
