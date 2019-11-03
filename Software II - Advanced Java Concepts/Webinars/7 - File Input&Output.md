---
Date: 2019/10/06
Length: 43:38
Note Taker: Alex Irvine
Speaker: Malcolm Wabara
---

Video: [File Input/Output](https://wgu.adobeconnect.com/pnm24wtxpb83/)

<u>**Summary**</u>:

Plan:

- Create Text files
- Append data to files
- read data from files

---

## File Input/Output Classes (00:32 - 3:19)

Classes for I/O:

- PrintWriter
- FileWriter
- File
- Scanner

Must import the `java.io.*` package to use these.  
`IOException` are thrown if there is an exception, so they must be caught if using these classes.

### PrintWriter

Used to create and write data to a file.  
**PrintWriter will overwrite an existing file if one exists.**

```java
//Create a printWriter
PrintWriter pwVariable = new PrintWriter("filename to create");

//Once created, this is how you write to a file
pwVariable.println(String);

//Must close once writing is complete
pwVariable.close();
```

---

## Programming exercise (3:20 - 17:58) - Create and Write data to file

(in main method)  
Make sure the main method `throws IOException`.

```java
//Filename & item variables
String fileName = "groceries.txt", item;

//Create a scanner object
Scanner keyboard = new Scanner(System.in);

//Get item count from user
System.out.print("How many items in shopping list? ");
int numItems = keyboard.nextInt();
keyboard.nextLine();                                    //clears the keyboard buffer

//Create and open file
PrintWriter outputFile = new PrintWriter(fileName);

//Prompt users for items, write to file
for (int i = 0; i < numItems ; i++) {
  System.out.print("Enter item[" + (i+1) + "]: ");
  item = keyboard.nextLine();
  outputFile.println(item);
}

//close file
outputFile.close();
```

---

## The FileWriter Class (18:00 - 19:30)

Used to create and append data to a file.  
`FileWriter fwVariable = new FileWriter("filename", true);`
[The teacer doesn't explain the `true`, says to just do it]

A FileWriter object is used as an argument for the PrintWriter object:  
`PrintWriter pwVariable = new PrintWriter(fwVariable);`  
[The teacher does not go into ANY detail why at this point].

You can use `print()` and `println()` to write, and `close()` to close.

---

## Programming exercise (19:30 - 21:52) - FileWriter

Add the following code to the code above:

```java
//do this before making the PrintWriter object in code above
//Create FileWriter
FileWriter fWriter - new FileWriter(fileName, true);

//Use the FileWriter in the PrintWriter
PrintWriter outputFile = new PrintWriter(fWriter);
```

Using this method, the newly written values are **appended** and not replacing.

---

## How to specify file location (22:00 - 25:30)

`"C:/folder/fileName.ext"` / or use relative address.  
It's good practice to put the files in a separate package than the source code.

---

## Reading data from a file (25:33 - 28:21)

Use `File` and `Scanner` classes.

```java
File fVar = new File ("filename");
Scanner sVar = new Scanner(fVar);
```

From here, use `nextLine()`, `nextInt()`, and `nextDouble()` to read in data.

The `hasNext()` method is sued to detect if there is a next line to read.  
Use a `While loop` & `hasNext()` to read through a file.

---

## Programming exercise (28:25 - 33:20)

```java
//Create filename & items variables.
String filename = "groceries.txt", item;

//Create file object & Scanner object
File file = new File(filename);
Scanner inputFile = new Scanner(file);

//Read all lines from file, displays it
while( inputFile.hasNext() ) {
  item = inputFile.nextLine();
  System.out.println(item);
}

//close file
inputFile.close();
```

---

## Programming exercise (33:29 - 40:10) - Reading numbers from a file

Useful for when you need to do math on numbers, and need them in a non-string format.

[The teacher has created a txt file with numbers on separate lines. No text is listed.]

```java
double product, sales = 0.0;

//Read all lines from file, totals sales
while( inputFile.hasNext() ) {
  product = inputFile.nextDouble();
  sales += product;
}
```

---

## Checking a File for Existence (40:11 - END)

Use File class's `exists()` method to check if a file exists. Returns true/false.

```java
//get file
File file = new File(filename);

//check if a file exists.  If not, SHUT DOWN THE PROGRAM
if ( !file.exists() ){
  System.out.println("File not found");
  System.exit(0);
}
```
