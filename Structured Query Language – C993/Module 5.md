---
Date: 2020/2/13
---

# Module 5 - Using Single-Row Functions to Customize Output

## 5.1 - Use Various Types of Functions That Are Available in SQL

<u>**Function**</u>: Functions have 3 characteristics:

1. They can accept parameters.
2. They can incorporate parameter data into a process.
3. They return a single answer as a result.

---

## 5.2 - Use Character, Number, Date, and Analytical (PERCENTILE_CONT, STDDEV, LAG, LEAD) Functions in SELECT Statements

<u>**DUAL table**</u>: Oracle has a "dummy" table that contains one column (DUMMY, VARCHAR2(1) ) with only one row, value 'x'.  
The DUAL table is used when you want to run a function and pass in a dummy variable.

### Character Functions

<u>**UPPER/ LOWER**</u>:  
Transforms parameter into either uppercase or lowercase.

```SQL
SELECT EMPLOYEE_ID
FROM   EMPLOYEES
WHERE  UPPER(LAST_NAME) = 'MCGILLICUTTY';
```

<u>**INITCAP**</u>:  
Transforms parameter into a mixed-case string, where only the first character is capitalized.

```SQL
SELECT INITCAP('napoleon'), INITCAP('RED O''BRIEN'), INITCAP('McDonald''s')
FROM   DUAL;

-- outputs

--  INITCAP('NAPOLEON') INITCAP('REDO''BRIEN') INITCAP('MCDONALD''S')
--  ----------------- ---------------------- ----------------------
--  Napoleon            Red O'Brien            Mcdonald'S
```

<u>**CONCAT (or ||)**</u>:  
Takes two parameters, s1 & s2, and combines them into one string.

```SQL
SELECT CONCAT('Hello, ', 'world!')
FROM   DUAL;

-- or

SELECT 'Hello, ' || 'world!'
FROM   DUAL;

-- outputs:  Hello, world!
```

<u>**LPAD/RPAD**</u>:  
Takes in 3 parameters, s1, n, s2(optional)  
Pads s1 with s2 character (space if ommited) to make s1 n long.

```SQL
SELECT RPAD('Chapter One - I Am Born',40,'.')
FROM   DUAL;

-- Outputs:
-- Chapter One - I Am Born.................
```

<u>**LTRIM / RTRIM**</u>:  
Takes parameters s1, s2(optional)  
Removes occurances of character s2 (space if ommited) from either the left side or right side of s1

```SQL
SELECT RTRIM('Seven thousand--------','-') Result
FROM   DUAL;

-- Output:
-- Seven thousand
```

<u>**LENGTH**</u>:  
Returns the length of the parameter string.

```SQL
SELECT LENGTH('Supercalifragilisticexpialidocious')
FROM   DUAL;

-- outputs:
-- 34
```

<u>**INSTR**</u>:  
Takes parameters s1, s2, pos (optional), n (optional).  
`s1` = string to search  
`s2` = substring (string in s1 to find)  
`pos` = position of s1 to start search (1 is first character)  
`n` = the occurrence of s2.

Looks for `s2` in `s1`, starting at `pos`. If `n` is specified, it will look for the `n`th occurrence of `s2` in `s1`. Returns the position found.

```SQL
SELECT INSTR('Mississippi','is',1,2)
FROM   DUAL;

-- outputs
-- 5
```

<u>**SUBSTR**</u>:

```SQL

```

<u>**SOUNDEX**</u>:  
Takes in a parameter and returns a SOUNDEX code.  
This code is used to determine how a word sounds, and can be used to compare two words and if they sound the same.

```SQL
SELECT SOUNDEX('Worthington'), SOUNDEX('Worthen')
FROM   DUAL;


-- outputs:

-- SOUNDEX('WORTHINGTON') SOUNDEX('WORTHEN')
-- ---------------------- ------------------
-- W635                   W635
```

### Numerical Functions

<u>**CEIL**</u>: Returns the smallest INT greater than the parameter, rounds up.  
<u>**FLOOR**</u>: Returns the largest INT that is less than or equal to the parameter, rounds down.  
<u>**ROUND**</u>: Takes numbers `n` and `i`(optional, default=0) and returns the truncated rounded version of that number to `i` precision.

<u>**TRUNC**</u>:  
Takes number `n` and optional `i` (default is 0), and truncates `n` to `i` precision.

```SQL
SELECT TRUNC(12.355143, 2), TRUNC(259.99,-1), TRUNC(259.99),
FROM DUAL;

-- Outputs:

-- TRUNC(12.355143,2)     TRUNC(259.99,-1)         TRUNC(259.99),
-- ---------------------- ----------------------   -------------
-- 12.35                  250                       259
```

<u>**REMAINDER**</u>:  
Divides parameter1 by parameter2, using ROUND, and returns the remainder.

```SQL
SELECT REMAINDER(9,3), REMAINDER(10,3), REMAINDER(11,3)
FROM   DUAL;

-- outputs

-- REMAINDER(9,3)       REMAINDER(10,3)      REMAINDER(11,3)
-- -------------------- -------------------- ----------------------
-- 0                    1                    -1
```

<u>**MOD**</u>:  
Divides parameter1 by parameter2 and returns the difference between the two using FLOOR.

```SQL
SELECT MOD(9,3), MOD(10,3), MOD(11,3)
FROM   DUAL;

-- outputs

-- MOD(9,3)               MOD(10,3)              MOD(11,3)
-- ---------------------- ---------------------- ----------------------
-- 0                      1                      2

```

### Date Functions

<u>**SYSDATE**</u>:  
Returns the system date, according to OS.

```SQL
SELECT SYSDATE FROM DUAL;

-- outputs:
-- 13 - FEB - 20
```

<u>**ROUND**</u>:  
Round function for the date, but the second parameter will be a constant value.

(Book goes into much more detail, but seems obvious at first read)

```SQL
SELECT SYSDATE TODAY,
ROUND(SYSDATE,'MM') ROUNDED_MONTH,
ROUND(SYSDATE,'RR') ROUNDED_YEAR
FROM DUAL;

-- outputs

-- TODAY ROUNDED_MONTH ROUNDED_YEAR
-- --------------------- --------------------- --------------------
-- 03-DEC-15 01-DEC-15 01-JAN-16
```

<u>**NEXT_DAY**</u>:  
Takes in a date & day-of-week as parameters, shows the next date.

```SQL
SELECT NEXT_DAY('31-MAY-19','Saturday')
FROM DUAL;

-- outputs:
-- 01 - JUN - 19
```

<u>**LAST_DAY**</u>:  
Returns the last day of the month that parameter falls in.

```SQL
SELECT LAST_DAY('14-FEB-20'), LAST_DAY ('20-FEB-21')
FROM DUAL;

-- outputs:

-- LAST_DAY( LAST_DAY(
-- --------- ---------
-- 29-FEB-20 28-FEB-21
```

<u>**ADD_MONTHS**</u>:  
Adds `n` months (2nd parameter) to the 'd' date (1st parameter), returns date.

```SQL
SELECT ADD_MONTHS('31-JAN-17',1),
ADD_MONTHS('01-NOV-17',4)
FROM DUAL;

-- outputs

-- ADD_MONTH ADD_MONTH
-- --------- ---------
-- 28-FEB-17 01-MAR-18
```

<u>**MONTHS_BETWEEN**</u>:  
Takes in two date paramters, and outputs how many months are in between the two dates.

```SQL
MONTHS_BETWEEN('01-JAN-17', '01-FEB-17') -1

MONTHS_BETWEEN('01-JAN-17', '01-MAR-17') -2

MONTHS_BETWEEN('10-AUG-17', '10-JUL-17') 1
```

<u>\*NUMTOYMINTERVAL\*\*\*</u>:

```SQL
SELECT NUMTOYMINTERVAL(27,'MONTH')
FROM DUAL;

-- NUMTOYMINTERVAL(27,'MONTH')
-- ---------------------------
-- 2-3
```

<u>**NUMTODSINTERVAL**</u>:

```SQL
SELECT NUMTODSINTERVAL(36,'HOUR')
FROM DUAL;

-- NUMTODSINTERVAL(36,'HOUR')
-- --------------------------
-- 1 12:0:0.0
```
