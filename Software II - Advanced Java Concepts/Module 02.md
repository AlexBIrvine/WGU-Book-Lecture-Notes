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
