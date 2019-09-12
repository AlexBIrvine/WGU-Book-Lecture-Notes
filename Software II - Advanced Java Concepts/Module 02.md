# Module 2 - Design Patterns and Principles

## 2.1 - Designing an Interface

Some rules about interfaces:

- Classes may `implement` multiple interfaces.
- Interfaces can `extend` other interfaces but not classes.
- Classes may not `extend` interfaces.

---

## 2.2 - Introducing Functional Programming

<u>**Functional Interface**</u>: An interface that contains a single abstract method.  
It can contain other things, but it must contain exactly one abstract method.

```java
@FunctionalInterface
public interface Sprint {
    public void sprint(Animal animal);
}

@FunctionalInterface
public interface Run extends Sprint {}

@FunctionalInterface
public interface SprintFaster extends Sprint {
    public void sprint(Animal animal);
}

@FunctionalInterface
public interface Skip extends Sprint {
    public default int getHopCount(Kangaroo kangaroo) {return 10;}
    public static void skip(int speed) {}
}
```

<u>**Lambda Expression**</u>: Block of code that gets passed around, like an anonymous method.

Two forms of Lamba Expressions. Both are equivalent, but 2 is more expressive:

```java
//Form 1
a -> a.canHop()

//Form 2
(Animal a) -> {return a.canHop();}
```

(The rest of the chapter goes into many examples of how to expand on these definitions, but it doesn't say why this is useful)

---

## 2.3 - Implementing Polymorphism

<u>**Polymorphism**</u>: The ability of a single interface to support multiple underlying forms.

When defining an object using the method `Object varName = new Object();`, the left side of the equals sign is the reference side.  
The reference can be a class or interface.  
Only the methods available to the reference will be available in the varName referenced.

So if you have the following code:

```java
public class Primate {
    public boolean hasHair() {
        return true;
    }
}
public interface HasTail {
    public boolean isTailStriped();
}
public class Lemur extends Primate implements HasTail {
    public int age = 10;

    public boolean isTailStriped() {
        return false;
}

```

And try to run:

```java
HasTail zoboomafoo = new Lemur()
System.out.println(zabomafoo.hasHair());
```

It will fail because `HasTail` reference doesn't know `hasHair()`

---

## 2.4 - Understanding Design Principles

<u>**Encapsulation**</u>: Combining fields and methods (mainly getters and setters) to "hide" away data and restrict it from being accessed directly.

<u>**Java Bean**</u>: A design principle for encapsulating data in an object in Java. It has particular rules for a class to be considered a java bean.  
Java Bean Rules:

1. Properties are private.
2. Getter for non-boolean properties begins with get.
3. Getters for boolean properties may begin with is or get.
4. Setter methods begin with set.
5. The method name must have a prefix of set/get/is followed by the first letter of the property in uppercase and followed by the rest of the property name.

<u>**Ia-a Relationship**</u>: When an object is an instance of another object, it's said to have a **Is-a Relationship** with that 2nd object.  
<u>**Has-a Relationship**</u>: When an object contains a particular property, it's said to have a **Has-a** relationship with that property.

---

## 2.5 - Working with Design Patterns

Patterns went over in this section:

- Singleton Pattern
- Immutable Objects
- Builder Pattern
- Factory Pattern

(Not going to expand on this section since I'm doing that in my notes on Head First Design Patterns)
