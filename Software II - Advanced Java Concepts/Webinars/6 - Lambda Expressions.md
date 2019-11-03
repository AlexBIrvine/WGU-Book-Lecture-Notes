---
Date: 2019/10/05
Length: 52:07
Note Taker: Alex Irvine
Speaker: Malcolm Wabara
---

Video: [Lambda Expressions](https://wgu.adobeconnect.com/pkmaqjbxi03a/)

<u>**Summary**</u>:

Plan:

- Understand Interfaces, functional interfaces and lambda expressions
- Define functional interfaces and write lambda expressions
- Use LocalVariables within lambda expressions

---

## Abstract Methods & Interfaces (00:50 - 06:00)

Abstract methods are methods without a body (only a header).  
Abstract methods **HAVE** to be overridden.  
Abstract methods must be specified in either an abstract class or interface.  
Template: `AccessSpecifier abstractMethodName ReturnType methodName(ParameterList);`  
Example: `public abstract void displayMessage(String s);`

Interface is a class that ONLY contains abstract methods.  
Defined like a class and cannot be instantiated.  
They are implemented by other classes.  
Once implemented, all abstract methods MUST be implemented.

Example:

```java
public interface InterfaceName {
    //abstract methods
}
```

---

## Functional Interfaces & Lambda Expressions (06:01 - 11:55)

<u>**Functional Interface**</u>: Contains only one abstract method.  
<u>**Lambda Expression**</u>: a method without a name. AKA Anonymous method.

A lambda expression creates an object that implements a functional interface and overrides it's abstract method.  
General Format: `parameter -> expression`  
**->**: Lambda operator.

Functional Interface Definition example:

```java
interface SquareInterface {
    int squareNumber(int n);
}
```

Lambda expression example:

```java
SquareInterface variable = parameter -> expression
```

Example to call it:

```java
variable.squareNumber(5);
```

[But... I feel like something is missing]

---

## Coding example (11:56 - 27:35) - Writing value returning lambda

(Same package, new file for interface)

```java
public interface GeneralInterface {
    int calculateSquare(int n);
}

public interface GeneralInteface2 {
    double calculateSquare (double n);
}

public interface GeneralInterface3 {
    String getMessage(String s);
}
```

(inside the class/main method)

```java
//Value returning lambda expression
GeneralInterface square = n -> n*n;                 //The return is implicit.
System.out.println(square.calculateSquare(5));      //returns 25

GeneralInterface2 square2 = n -> n*n;
System.out.println(square2.calculateSquare(5));     //returns 25.0

GeneralInterface3 message = s -> s + "!";
System.out.println(message.getMessage("Hello"));    //prints "Hello!"
```

---

## More Lambda Expressions (27:35 - 30:44) - void lambda expressions [but some of these are not void...]

Void lambda expressions return nothing.

<u>**Multiple Parameters**</u>:  
`(parameter1, parameter2) -> parameter1*parameter2`

<u>**No Parameters**</u>:  
`() -> System.out.println("Hello World");`

<u>**Explicit parameter (optional)**</u>:  
`(int parameter) -> parameter * parameter;`

<u>**Multiple statements (MUST specify return statement)**</u>:

```java
(int parameter) -> {
    int x = parameter * 2;
    return x;
}
```

---

## Coding examples again (30:45 - 46:20)

(Interface file from above)

```java
// void abstract method
public interface GeneralInterface4 {
    void printMessage(String s);
}

//multiple parameters
public interface GeneralInterface5 {
    int calculateSum(int a, int b);
}

//no parameters
public interface GernalInterface6 {
    void printMessage();
}

//multiple statements
public interface GeneralInterface7 {
    int calculateSquare(int n);
}
```

(inside the class/main method)

```java
// void lambda expression with one parameter
GeneralInterface4 message = s -> System.out.println(s + "!");
message.getMessage("Alex");                                     //prints "Alex!"

GeneralInterface5 sum = (x, y) -> x + y;
System.out.println(sum.calculateSum(1, 2));                     //prints "3"

GeneralInterface6 message = () -> System.out.println("Hello!");
message.printMessage();                                         //prints "Hello!"

GeneralInterface7 square = n -> {
    int x = n * n;
    return x;
}
System.out.println(square.calculateSquare(5));                  //prints 25
```

---

## Accessing local variables within a lambda expression (46:23 - END)

A local variable must be declared as `final` before it can be used.

(inside the class/main method)

```java
//Using local variable in lambda expression
final int num = 5;

//Reuse previous example
GeneralInterface7 square2 = n -> {
    int x = n * n;
    return x;
}
System.out.println(square2.calculateSquare(num));                  //prints 25
```
