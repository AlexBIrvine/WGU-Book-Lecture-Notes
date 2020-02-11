---
Date: 2020/2/11
---

# Module 3 - Manipulating Data

## 3.1 - Truncate Data

<u>**Truncate command**</u>: Truncate is used instead of `DELETE` when you want to remove the contents of a table without impacting the index structure or child tables.  
It will:

- Remove all rows in a given table
- Removes all data in associated indexes
- Does **NOT** fire DML triggers
- Performs an implicit commit

```SQL
TRUNCATE TABLE <table name>
```

Since this doesn't fire DML triggers, you will need to call `CASCADE` when restricted by the FOREIGN KEY constraints.  
This command also cannot be rolled back.

---

## 3.2 - Insert Rows into a Table

<u>**INSERT**</u>: Used to add rows to a table.  
Typically adds one row at a time, but can add multiple when referencing from another point in the database.

```SQL
1   INSERT INTO CRUISES
2   (CRUISE_ID, CRUISE_TYPE_ID, CRUISE_NAME, CAPTAIN_ID, START_DATE, END_DATE, STATUS)
3   VALUES
4   (1, 1, 'Day At Sea',101, '02-JAN-10', '09-JAN-10','Sched');
```

**Note:**

- The order of the column names in line 2 does not have to match the order found in the table itself.
- The columns in line 2 do not have to be all the columns in the table.
- **IF** the values in line 2 match the values and order of the columns in the table, line 2 can be omitted.
- CONSTRAINTS will be checked, and a runtime error can be thrown.
- ORACLE will perform **implicit conversions** where possible. The following statement is valid:

```SQL
INSERT INTO CRUISES (CRUISE_ID)
VALUES ('101'); --Converts VARCHAR2 into NUMBER implicitly.
```

---

## 3.3 - Update Rows in a Table

<u>**UPDATE**</u>: Modifies existing data, works on one table at a time.

```SQL
UPDATE  CRUISES
SET     CRUISE_NAME = 'Bahamas',
        START_DATE  = '01-DEC-11'
WHERE   CRUISE_ID = 1;
```

**Note:**

- Columns not referenced will not be changed.
- Omitting the `WHERE` keyword will **not** throw an error & update will operate on **ALL** table rows.
- CONSTRAINTS will be checked, and a runtime error can be thrown.
- Expressions can be used to calculate a value. The following statement is valid:

```SQL
UPDATE  COMPENSATION
SET     SALARY = SALARY * 1.03,
        LAST_CHANGED_DATE = SYSDATE
WHERE   EMPLOYEE_NUMBER = 83;
```

---

## 3.4 - Delete Rows from a Table

<u>**DELETE**</u>: Removes existing rows.

```SQL
DELETE FROM PROJECT_LISTING
WHERE       CONSTRUCTION_ID = 12;
```

(No further notes were given. Matches the same rules for `WHERE` as the UPDATE command)

---

## 3.5 - Control Transactions

This sections covers 3 statements:

1. <u>**COMMIT**</u>: Saves changes to the database since the session began or since the most recent commit event in the session, whichever is more recent.
2. <u>**ROLLBACK**</u>: Undoes changes to the database performed within a session, back to the last "commit" point in the session.
3. <u>**SAVEPOINT**</u>: Temporarily sets an optional point, marker.

### COMMIT

- Commit is used to save changes made by `INSERT`, `UPDATE` & `DELETE` statements.
- changes saved this way are permanent and cannot be undone using `ROLLBACK`.
- There are two types of commits, explicit & implicit.
  - **Explicit** commits are done when the COMMIT statement is exectuted.
  - **Implicit** commits are done automatically after certain database events.
- Changes made before commits can be seen by the current user, but not by other users accessing the same database.

<u>**Implicit commits**</u>: They are done after any DDL statement occurs (CREATE, ALTER, DROP, etc.,) or after a normal exit from Oracle tools (SQL\*Plus / SQL Developer)

### ROLLBACK

A ROLLBACK undoes any DML statements that were performed since the last commit.  
Simple as that.

### SAVEPOINT

SAVEPOINT allows you to mark a place in execution to be able to ROLLBACK to, without needing to commit.

```SQL
1   COMMIT;
2   UPDATE SHIPS SET HOME_PORT_ID = 21 WHERE SHIP_ID = 12;
3   SAVEPOINT MARK_01;
4   UPDATE SHIPS SET HOME_PORT_ID = 22 WHERE SHIP_ID = 12;
5   SAVEPOINT MARK_02;
6   UPDATE SHIPS SET HOME_PORT_ID = 23 WHERE SHIP_ID = 12; --This line is not committed
7   ROLLBACK TO MARK_02;
8   COMMIT;
```

Rules for SAVEPOINTS:

- They must all include a name.
- You cannot duplicate names within a single transaction.
- SAVEPOINTS are erased from memory after COMMIT is ran.
