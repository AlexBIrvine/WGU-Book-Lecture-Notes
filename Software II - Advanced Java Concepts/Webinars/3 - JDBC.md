---
Date: 2019/09/22
Note Taker: Alex Irvine
Speaker: Malcolm Wabara
---

Video: [JDBC (Java Database Connectivity)](https://wgu.adobeconnect.com/pvom9qkr9xxn/)  
JDBC = Java Data Base Connectivity

<u>**Summary**</u>:  
This webinar goes into detail on how to setup a JDBC driver, create a class to connect to a database, and close the database.  
This will **NOT** go into interacting with the database.

---

## Connecting to a database

use `getConnection()` from `DriverManager` class.  
This will return a `Connection` object.  
After using the database, close it using the `close()` method.

---

## JDBC Driver

You will also need a [JDBC driver](https://dev.mysql.com/downloads/file/?id=480091)  
[5:00 - 7:50 in video]In NetBeans, make a new package called lib, and move the driver into it through windows explorer. The driver will be a .jar file.

---

## Java Code

```java

public class DBConnection {
    private static final String databaseName = "U05NCh";
    private static final String DB_URL = "jdbc:mysql://52.206.157.109/" + databaseName;
    private static final String userName = "U05NCh";
    private static final String password = "";
    private static final String driver = "com.mysql.jdbc.Driver";
    public static Connection conn;

    public static void makeConnection() throws  classNotFoundException, SQLException, Exception {
        //Create a connection object
        Class.forName(driver);
        conn = (Connection) DriverManger.getConnection(DB_URL, userName, password);
        System.out.println("Connection successful");
    }

    public static void closeConnection() throws ClassNotFoundException, SQLException, Exception {
        conn.close();
        System.out.println("connection closed");
    }
}
```

In your java class that runs this code, the `Main()` method that uses this needs to also throw the same exceptions as `makeConnection()` and `closeConnection()`.
