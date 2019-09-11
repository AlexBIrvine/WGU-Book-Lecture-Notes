# Module 1 - Advanced Class Design

## 1.2 - Using instanceof

`a instanceof b` returns `true` if `a` is an instance of `b`, subclass of `b`, or implements interface `b`.

---

## 1.3 - Understanding Virtual Methods

Virtual methods are methods called by one class of another? The book isn't very clear, but according to it:

```
"They are just regular non-static methods.
Java looks for an overridden method rather than necessarily using the one in the class that the compiler says we have.
The only thing new about virtual methods on the OCP is that Oracle now calls them virtual methods in the objectives"
```

---

## 1.4 - Annotating Overridden Methods

The `@` symbol means annotation in Java, which is metadata to be used by the compiler.  
`@Override` indicates the following method is overriding something in the superclass/interface.  
If the annotation is used and the method does not override anything, a warning will be thrown.

---

## 1.5 - Coding equals, hashCode, and toString

Common methods to override from the Object Superclass are: `toString()`, `equals()` & `hashCode()`.  
There is a common library that has "Builders" for these methods called [Commons Lang](http://commons.apache.org/proper/commons-lang/)  
If you override `equals()`, your are expected to override `hashCode()`.

---

## 1.6 - Working with Enums

`Enums` are a fixed set of constants. For sets that you know the values of at compile time, you can create an enum.  
Examples of common enums are days of the week, seasons in a year, months in a year, etc.,

```Java
public enum Season {
   WINTER, SPRING, SUMMER, FALL
}
```

You can also add `Constructors`, `Fields` & `Methods` to enums:

```Java
public enum Season {
    WINTER("Low"), SPRING("Medium"), SUMMER("High"), FALL("Medium");
    private String expectedVisitors;

    private Season(String expectedVisitors) {
       this.expectedVisitors = expectedVisitors;
    }

    public void printExpectedVisitors() {
       System.out.println(expectedVisitors);
    }
}
```

---

## 1.7 - Creating Nested Classes

4 Types of nested classes:

1. <u>**Member Inner Class**</u>: defined at the member level of a class (the same level as the methods, instance variables, and constructors).
2. <u>**Local Inner Class**</u>: nested class defined within a method.
3. <u>**Anonymous Inner Classes**</u>: local inner class that does not have a name.
4. <u>**Static Nested Classes**</u>: static class defined at the member level.

### Member Inner Classes

These are declared like a normal class inside another class, and can access all members of the outerclass (including private members).

Example of Member Inner Class:

```Java
public class Outer {
  private String greeting = "Hi";

  protected class Inner {
    public int repeat = 3;
    public void go() {

    for (int i = 0; i < repeat; i++)
       System.out.println(greeting);
    }
  }
}
```

Example of class being constructed & used:

```java
public static void main(String[] args) {
   Outer outer = new Outer();
   Inner inner = outer.new Inner();   // create the inner class
   inner.go();
}
```

To call `this` on the outer class from the inner class, use this syntax: `Outer.this.member`. This is mostly useful if the member of both inner/outer classes share a name.

### Local Inner Classes

These are classes declared inside methods. They do not exist until the method is called, and stop existing when the method is complete.

Example:

```java
public class Outer {
 private int length = 5;

 public void calculate() {
   final int width = 20;

   class Inner {
     public void multiply() {
       System.out.println(length * width);
     }
   }

   Inner inner = new Inner();
   inner.multiply();
 }

 public static void main(String[] args) {
   Outer outer = new Outer();
   outer.calculate();
 }
}
```

### Anonymous Inner Classes

A Local Inner Class created anonymously.

Example:

```java
public class AnonInner {
  abstract class SaleTodayOnly {
    abstract int dollarsOff();
  }

  public int admission(int basePrice) {
    SaleTodayOnly sale = new SaleTodayOnly() {  //Here it is made
      int dollarsOff() { return 3; }            //Overriding abstract method
    };

    return basePrice - sale.dollarsOff();
  }
}
```

### Static Nested Classes

A static class definded at member level.  
(The book doesn't give a useful example of how this is used. It only goes into the details of what does/n't compile or run)

![1.1](./img/1.1.jpg)
