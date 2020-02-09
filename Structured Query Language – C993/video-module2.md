---
Date: 2020/2/9
Lecturer: Dr. Sewell
Note Taker: Alex Irvine
Length: 40:27
---

Video: [Lesson1: Using DDL Statements to Create and Manage Tables](https://wgu.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=ccec8a74-1483-42d8-8b5b-a8e6011a6b00)

<u>**Summary**</u>:

---

## Start (00:50)

There are more than table objects that you can create in a database, but this lesson will focus on tables.

<u>**Schema**</u>: A collection of objects owned by a user account.

## Create a simple table (3:28)

DDL main commands:

- CREATE
- ALTER
- DROP

<center>CREATE example</center>

```SQL
CREATE TABLE work_schedule
(work_schedule_id   NUMBER,
 start_date         DATE,
 end_date           DATE);
```

There is a list of `reserve words` that you cannot use. These are the commands that are used by SQL.

When naming, you _can_ use quotes to include spaces, but that can cause problems.

<center>Example with constraints</center>

```SQL
CREATE TABLE cruises
( cruise_id           NUMBER,
  cruise_type_id      NUMBER,
  cruise_name         VARCHAR2(20),
  captain_id          NUMBER NOT NULL,
  start_date          DATE,
  end_date            DATE,
  status              VARCHAR2(5) DEFAULT 'DOCK',
  CONSTRAINT cruise_pk PRIMARY KEY (cruise_id) );
```

<u>**Note**</u>:

- `DEFAULT 'DOCK'` will set the status to 'DOCK' if no value is provided.
- `NOT NULL` is used on captain_id, forcing a value.
- `PRIMARY KEY` is set.

<u>**DESCRIBE command**</u>: You can use `DESCRIBE -table name-` to get details about a table.

---

## Data Types (9:32)

<u>**CHAR(n)**</u>: Will give you padded spaces.  
<u>**VARCHAR2(n)**</u>: Does not give padded spaces.  
<u>**NUMBER(n,m)**</u>: Arguments add precision. m refers to digits after the decimal.  
<u>**DATE**</u>: Date can be parsed out to YEAR, MONTH, etc.,  
<u>**TIMESTAMP(n)**</u>:  
<u>**TIMESTAMP(n) WITH TIME ZONE**</u>:  
<u>**TIMESTAMP(n) WITH LOCAL TIME ZONE**</u>:  
<u>**INTERVAL YEAR(n) TO MONTH**</u>:  
<u>**INTERVAL DAY(n1) TO SECOND(n2)**</u>:  
<u>**BLOB**</u>: Binary large object. ERD, jpeg, video, etc.,  
<u>**CLOB**</u>: Character large object. Like a book.  
<u>**NCLOB**</u>: National CLOB, used for storing language as well.

If you do not name a primary key, ORACLE will generate a system key.

The book goes into many examples of simple tables created with various constraints.  
Read and be familiar with section `2.5`.

Inline vs out of line. The speaker _briefly_ mentioned this, but the book goes into detail.  
**REVIEW LATER**

![Constraint Review](./img/2-4.jpg)

(Most of the remaining notes are the speaker copying code, running it, and showing the results.  
I will not be taking notes on these, for more details see book notes instead.)
