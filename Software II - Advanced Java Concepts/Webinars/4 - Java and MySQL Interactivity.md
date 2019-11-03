---
Date: 2019/10/01
Length: 1:22:55
Note Taker: Alex Irvine
Speaker: Malcolm Wabara
---

Video: [Java and MySQL Interactivity](https://wgu.adobeconnect.com/pg0j5gbae75p/)

<u>**Summary**</u>:

Plan:

- Catch MySQL Exceptions
- Compare SQL and Dave Data Types
- Understand the Statement and ResultSet Objects
- Execute MySQL statements in Java
- Create a Query and ResultSet Management Class

---

## Catch MySQL Exceptions

Occurs when there is an error in SQL statement.

You can either `throw` exceptions at the method level, or surround statements in a `try-catch` block.
Catching a basic `Exception` will catch all exceptions.

```java
try {
    DBConnection.makeConnection();
} catch (Exception ex) {
    System.out.println("Error: " + ex.getMessage());
}
```

---

## Compare SQL and Dave Data Types

![4.1](./img/4.1.jpg)

---

## Understand the Statement Object

A `Statement Object` provides methods for executing SQL statements in Java.

Psuedocode:

```java
Statement variableName = connectionObjectReference.createStatement();
```

Real Code:

```java
Statement connStatement = conn.createStatement();
```

<u>**executeQuery()**</u>: Used for SELECT statements.  
<u>**executeUpdate()**</u>: Used for INSERT, UPDATE, DELETE statements.

---

## Understanding the ResultSet Object

Contains one or more columns and one or more rows.  
Think of a result as a table.  
Created when you call the `executeQuery()` method.

```java
ResultSet result = connStatement.executeQuery("SQL statement");  //stetementObjectReference
```

You will receive an `Internal Cursor` with every ResultSet.

ResultSet Methods:  
<u>**next()**</u>: Advances internal cursor to access data in next row.  
Returns `true` when it jumps to another row, `false` when it can't.

<u>**getString() / getDouble() / getInt()**</u>: Retrieves contents of cells, based on data type.

---

## Programming exercise (18:21 - 25:05)

Modifying code from last webinar. All of this code will be handled in `Main()` method.

```java
public static void main(String[] args) {
    try {
        //connects to database, updates conn property
        DBConnection.makeConnection();

        //creates statement
        Statement stmt = conn.createStatement();

        //Write SQL statement
        String sqlStatement = "SELECT * FROM employee_tbl";

        //Create ResultSet object with executeStatement.
        ResultSet result = stmt.executeQuery(sqlStatement);

        //Closes connection
        DBConnection.closeConnection();
    }
    catch (Exception ex) {
        System.out.println("Exception: " + ex.getMessage());
    }
}
```

---

## MySQL Workbench exercise (25:05 - 28:12)

_The speaker then goes into MySQL Workbench to create the employee table.  
There is a Query.txt file you can download from the webinar to create the table.  
I am not going through the trouble to do this in these notes._

_The end result looks like this:_

![4.2](./img/4.2.jpg)

---

## Programming exercise (28:12 - 36:30) - Retrieve records

```java

    // Get all records from ResultSet object

    while(result.next()) {  //loops through until it gets to the end
        system.out.println(result.getInt("EmployeeID"));
        system.out.println(result.getString("EmployeeName"));
        system.out.println(result.getString("Department"));
        system.out.println(result.getDate("HireDate"));     // getDate() is separate from getTime()
        system.out.println(result.getTime("HireDate"));     // getDate() is separate from getTime()
    }
```

---

## Programming exercise (37:31 - 53:00) - Insert records

Before try-catch block in main()

```java
// Create variables
int employeeID;
String employeeName, department, hireDate;      //dates can be entered as a string into a database.

//Create Scanner object, collect data from console
Scanner keyboard = new Scanner(System.in);

System.out.print("Enter employee name: ");
employeeName =  keyboard.nextLine();        // nextLine() is used to collect strings.

System.out.print("Enter department: ");
department =  keyboard.nextLine();

System.out.print("Enter hire date (yyyy-mm-dd): ");
hireDate =  keyboard.nextLine();

```

Inside try block, after `Statement stmt = conn.createStatement();`:

```java
// SQL INSERT statement
String sqlInsertStatement = "INSERT INTO employee_tbl(EmpoloyeeName, Department, HireDate)" +
                    "VALUES(" +
                    "'" + employeeName + "'," +
                    "'" + department + "'," +
                    "'" + hireDate + "'" +
                    ")";

// Execute INSERT statement
stmt.executeUpdate(sqlInsertStatement);
```

---

## Programming exercise (53:48 - 60:07) - Delete records

```java
//Scan in empoloyee ID
System.out.print("Enter id: ");
employeeID = keyboard.nextInt();

//Execute DELETE FROM statement
String sqlDeleteStatement = "DELETE FROM employee_tbl WHERE EmployeeID = " + String.valueOf(employeeID);
```

---

## Programming exercise (60:07 - END) - User-Defined Query class

```java
public class Query {
    private static String query;
    private static Statement stmt;
    private static ResultSet result;

    public static void makeQuery(String q) {
      query = q;

      try {
        //Create statement object
        stmt = conn.createStatement();

        // Determine query execution, execute
        if (query.toLowerCase().startsWith("select"))
          result = stmt.executeQuery(query);
        else
          result = stmt.executeUpdate(query);

      }
      catch (Exception ex){
        System.out.println("Error: " + ex.getMessage());
      }
    }

    public static ResultSet getResult() {
      return result;
    }
}
```
