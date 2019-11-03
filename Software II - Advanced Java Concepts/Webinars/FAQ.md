## Interface

**Where can I get information on building a GUI and Scene Builder?**

- Check out this resource from Lynda.com:  
  [Java FX and Scene Builder tutorial](https://docs.oracle.com/javase/8/scene-builder-2/get-started-tutorial/jfxsb-get_started.htm)  
  [Code Makery Java FX Tutorial](http://code.makery.ch/library/javafx-8-tutorial/part2/)

---

## Database

### **Is the database supposed to be empty? Is there a script to load data?**

- The database is created with no information. There is a script in the announcement section of the course that you may use to import data. Check out MySQL workbench for assistance with the SQL portion of the assessment.

### **What are the tables increment type and reminder used for?**

- These tables are not needed to successfully complete the project. The database is meant to simulate a database that exists before this project, and therefore was not written just for this project. That is why there are tables that are not needed. There is a script in the course tips that will drop these tables (and add auto-increment on all the primary keys)

### **Can I make changes to the database tables? There seems to be a primary key missing…**

- The only change you may make is to add auto-increment on all the primary keys and to drop the increment and reminder tables. There is a script in the course tips that will do these items for you.

### **What is a ‘consultant’ for the Appointments by Consultant report?**

- Consultant is synonymous with user in this case. To relate the user to an appointment, we recommend that you use the createdBy column in the appointment table. (And document that you did so!)

### **What should I enter for <some information into the database>?**

- We understand that the information entered into the database may vary by student. Any decisions that you make about the data in the database tables should be included in your documentation.

### **I am getting a ClassNotFoundException and my program will not connect to the database.**

- A ClassNotFoundException usually means that the run configuration is not setup to include the JDBC library. Here are instructions to include the library in NetBeans:

1. Right click the coffee cup icon for your project in the projects window
2. Choose properties
3. Choose libraries from the left list
4. Click add Library
5. Choose MySQL JDBC Driver
6. Click Ok enough times to get back to the main screen

### **I’m using stored procedures, and I can’t get the time to display in the correct time zone. (Note that using stored procedures is optional!)**

- There is a bug in the JDBC driver that when you use a stored procedure to update timestamp fields it always saves the date in local time. So if you are attempting to save the time in UTC, a stored procedure won’t allow you to do that. There is a patch, but there is no guarantee that the evaluators will have that patched driver.  
  For more information, go here: http://www.smapp.com.hk/blog/?p=29
  Then save the configuration.
  \*If you are unable to get the current version driver (5.1.41 or later) working in NetBeans, try installing an older version of the jdbc driver. This seems to be a NetBeans only problem.
  Please download the connector from the following link and give it a try: https://mvnrepository.com/artifact/mysql/mysql-connector-java/5.1.21

### **The rubric wants me to “capture the type of appointment,” but type is not a field in the appointment table. How do I handle this?(Note that this question refers to an older version of the database. Do not be concerned if you do not see this issue in your database!)**

- You can use another field in the appointment table such as description. Then you can populate that field with some different types of appointments (“Initial consultation” for instance)

### **I’m having trouble converting my timestamp for the database. Where can I get more information?**

- A student posted this question on Stack Overflow, and got a great response!
  https://stackoverflow.com/questions/44443327/timestamp-conversion-to-instant-in-java-adds-unnecessary-time-offset

### **The book says that we shouldn’t use a DriverManager, but then all the code examples use DriverManager! How can I use a data source like the book recommends?**

- There is an example in the [code repository](https://drive.google.com/open?id=1A2jTo8yOzKRuPuZTnMbPwxaI-RUeYue5) called C195DatabasewithDS.

---

## Frameworks and External Code

**Can I use [insert framework]?**

- In order to keep the grading of the projects down to a reasonable time frame, please do not use external frameworks which require additional steps/files for compilation.

**Can I use external libraries or code?**

- All code for this program should be built by you (refer to the project specifications a description of how to give credit for any tutorial code that you may use. ) Please do not use code for pre-built calendars or screen widgets unless they are part of the regular API.
  The reason for this is that your evaluator may not have the same libraries and is under no obligation to install libraries since they use their own devices for evaluation. If they don’t, this will delay your evaluation, and it is likely you’d have to take the libraries out anyway.

**Where can I get the jar needed for the database connection?**

- We have a copy on our Google drive here: https://drive.google.com/open?id=0BxOtySSo7z-WYU95TWl2SVoyVW8

---

## Questions about Requirements

**Section A requires a login form that can determine the user’s location and translate the login and error control into two languages. How is that tested?**

- These are the steps that the evaluator will take:

1. Figure out what the second language is that the student coded into the application
2. Go to our computer settings and change the region to one with that language ie. Spain, France, etc.
3. Open the application
4. Determine if the text has changed to the new language (Note that the text might not be right but as long as the evaluator sees the text change, it’s fine. We recommend using Google Translate if you don’t read and write a second language.)

- Note that this is the only way this section can be satisfied. It is NOT sufficient to allow the user to choose their locale!
  While it does not explicitly state to change the labels on the login GUI form based on locale, it is expected that this will be done for a GUI application (only for the login form!). If you choose to write a console app, then the user prompts should also be in the appropriate language based on locale. (again, only for the login prompts)

**Section A: How do I get the locale codes for the region/language I’ve chosen?**

- This link lists all of the codes:
  http://www.science.co.il/language/Locale-codes.php

**Section B: What does “enter and maintain customer records” mean? Do I need to be able to update and delete customer records? (This is from an older version of the task. Do not be concerned if you do not see this.)**

From evaluation:

- The application needs to be able to not only add new clients as needed by the user but also update clients that already exist. Some [evaluators] said that the ability to delete a client is also needed but I would make an argument that if the application is done right they don’t need to delete a client [from the table] because they can update them to inactive.

**Section D: Do I need to provide a graphical calendar, or is listing the appropriate appointments enough?**

- It is enough to display the relevant appointments (those in the current month or week) in a TableView. You could have a toggle switch like a radio button group to allow the user to choose between the two options.

**Section E: What do the directions mean when they say that the appointment times must change according to the user’s time zone?**

- To evaluate that portion of your project, the evaluator will run your application in their own time zone, and then change their system’s time zone. They’ll run your application again and expect your appointments to reflect the new time zone. We recommend that you mimic this test! Note that if you use the new date/time classes (LocalDateTime, ZonedDateTime, etc), you don’t have to worry about daylight savings time because those classes handle it for you!

**Section F requires two methods of exception control. What are examples of exception controls?**

Based on the material, different examples of exception control would be:

- try/catch blocks
- try with resources blocks
- assertions
- throw/throws clauses

Most projects will contain try/catch and try with resources but this is a good chance to work with assertions and design for throw/throws clauses.

**Section F also lists a requirement of having an exception control to prevent scheduling an appointment outside a business hours. How do I handle that within the different time zones?**

- Typically, business hours are 8 - 5, so it is reasonable that that is the constraint you place on adding appointments. The constraint should be checked only when the user adds an appointment. So, for instance, if a user adds an appointment for 4 pm in Eastern time, that is fine and should add to the database. When you switch to London time (which is in the UTC time zone), that appointment will show a 9 pm start time, and that’s ok.

**And while we’re on business hours, what exactly are business hours?**

- Business hours are whatever you like, within reason. For instance, you may allow weekend hours, but be sure to document that that’s what you’re doing. Two am appointments are going to be considered outside business hours regardless of documentation though!

**Section H: Do I need code that checks for appointments once upon login and displays a message if there are any 15 min away? Or do I need to use another thread to handle thread.sleeps and constantly check for appointment times?**

From evaluation:

- I have seen it both ways as well and passed it using both ways.
  With that being said, the way that I would suggest is to do the alerts at login. Below is an example:
  There is an appointment for the user at 2PM in their current time zone. The user logs in somewhere between 1:45pm and 1:59:59 (in the current time zone) and they get an alert that provides enough detail that they know what the meeting is. The alert can’t be vague or too basic. It needs to let the user know enough information that they could reasonably understand that the alert if for a specific meeting.

· Example: “You have a meeting” (Too Vague ) //Not Ok
· Example: “You have a meeting with Client X” (More specific ) //Ok
· Example: “You have a meeting with Client X at 2PM” (Most specific) //Best

**Section I: What do they mean by report? Do I need to have something print out? Sent to a file?**

- It is sufficient to display your report on the screen. If you’re using JavaFX, you could do this in a TableView or a TextArea, for instance.

**For the consultant report, do I need to print for all consultants, or just one?**

- We recommend that you print the report for all consultants at one time.

**Where should I put the database methods in my code?**

- Here is a link to the recording of the [C195 Organizing Your Code Webinar Blast](https://wgu.adobeconnect.com/pet2xqw9rkbj/).
