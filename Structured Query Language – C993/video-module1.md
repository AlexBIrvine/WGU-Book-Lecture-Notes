---
Date: 2020/2/8
Lecturer: Dr. Sewell
Note Taker: Alex Irvine
Length: 41:29
---

Video: [Lesson1: Oracle and Structured Query Language(SQL)](https://wgu.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=262e223a-5075-4214-a89b-a8e601095284)

<u>**Summary**</u>:

- This is a review of the basics of the previous classes (what is a database, ERD, SQL, relationships, etc.,)
- Notes will be sparse because nothing is new.
- This seems to be just watching the teacher skim the book and read what he's skimming.

## Start (00:33)

(Webinar still says C746)

### Plan

The purpose of these videos are to help you study in "the most expeditious manner".  
Plan to study 2 chapters per week.

---

## Lesson 1 (02:50)

Oracle is very ANSI SQL compliant, and sits on the ANSI SQL committee body.  
Oracle is close to ANSI, and very transferable to other SQL engines.

Go to Oracle's website, create an account, and download the software.  
**`SQL*Plus` & `Oracle SQL Developer` are the software Dr. Sewell will use in the course.**

The exam is timed, you have 82 seconds per question.  
The exam is -071.

Most of the material in this lesson will be familiar since WGU made us take 2 database classes already.

<u>**Reminder**</u>:  
Entity = Table

---

## Entities & Relationships (08:34)

<u>**Crow's foot notation**</u>: Shows up when using a one-to-many relationship.  
<u>**Attributes**</u>: The "columns" of the table. (Ex., Name, number, address)  
<u>**Primary Key**</u>: Unique identifier.

Resolve a `many-to-many` relationship by creating a middle table to link the two.

---

## Database Normalization (19:33)

| Level of Normal Form | Abbreviation |                                                               Characterized By                                                                |
| :------------------: | :----------: | :-------------------------------------------------------------------------------------------------------------------------------------------: |
|  First normal form   |     1NF      |                                             No repeating groups; all tables are two-dimensional.                                              |
|  Second normal form  |     2NF      |                                  1NF plus each data element is identified by one non-composite primary key.                                   |
|  Third normal form   |     3NF      |                      2NF plus all tables contain no data other than that which describes the intent of the primary key.                       |
|      Boyce-Codd      |     BCNF     | A slightly modified version of 3NF designed to eliminate structures that might allow some rare logical inconsistencies to appear in the data. |
|  Fourth normal form  |     4NF      |                      BCNF plus additional logic to ensure that every multivalued dependency is dependent on a superkey.                       |
|  Fifth normal form   |     5NF      |                                4NF plus every join dependency for the table is a result of the candidate keys.                                |

<u>**Lecture comments**</u>:

- 1NF, make columns atomic (only zip codes in zip code column)
- 2NF, Make primary key "good"?
- Really 7 normal forms, but beyond 5 is not on the test.
- **Most databases are not past 3NF since table joins take time.**

---

## The SQL language (23:20)

### <center>Major SQL commands</center>

| SQL Command        |                     Description                      | Type |
| :----------------- | :--------------------------------------------------: | :--: |
| SELECT             |             Retrieves data from a table              | DML  |
| INSERT             |               Adds new data to a table               | DML  |
| UPDATE             |          Modifies existing data in a table           | DML  |
| DELETE             |          Removes existing data from a table          | DML  |
| CREATE object_type |    Creates a new database object, such as a table    | DDL  |
| ALTER object_type  | Modifies the structure of an object, such as a table | DDL  |
| DROP object_type   | Removes an existing database object, such as a table | DDL  |

<u>**DDL**</u>: Data Definition language.  
<u>**DML**</u>: Data Manipulation language.  
<u>**TCL**</u>: Transition Control Language.

### <center>All commands covered on exam</center>

| Type |  Command  |
| :--: | :-------: |
| DDL  |  CREATE   |
|      |   ALTER   |
|      |   DROP    |
|      |  RENAME   |
|      | TRUNCATE  |
|      |   GRANT   |
|      |  REVOKE   |
|      | FLASHBACK |
|      |   PURGE   |
|      |  COMMENT  |
| DML  |  SELECT   |
|      |  INSERT   |
|      |  UPDATE   |
|      |  DELETE   |
|      |   MERGE   |
| TCL  |  COMMIT   |
|      | ROLLBACK  |
|      | SAVEPOINT |

---

## Purpose of DDL (28:50)

Create, alter, or drop ) database objects.

---

## Purpose of DML (31:29)

Select, insert, update, delete, merge.

---

## Build a SELECT statement (32:27)

<center>Create and populate table</center>

```SQL
CREATE TABLE SHIPS
(SHIP_ID    NUMBER,
SHIP_NAME   VARCHAR2(20),
CAPACITY    NUMBER,
LENGTH      NUMBER );

INSERT INTO SHIPS (SHIP_ID, SHIP_NAME, CAPACITY, LENGTH)
VALUES (1,'Codd Crystal', 2052, 855);
```

<center>The SELECT statement</center>

```SQL
SELECT   SHIP_NAME, CAPACITY, LENGTH
FROM     SHIPS;
```

(The lecturer then goes into demonstrating this code in `SQLPLUS`)

---

## Summary (36:50)

The end! What to study hard:

- DML, DDL, TCL & their differences.
- How the test will be conducted.
- Don't forget to check out the book's quiz/cards.
  - **Note taker's note**: Ignore the cards. They are very stupid flash cards, make your own.
