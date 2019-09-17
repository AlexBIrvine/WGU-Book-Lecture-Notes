# Module 3- Generics and Collections

## 3.2 - Working with Generics

Generally speaking, generics are those classes, methods and interfaces that have the diamond/angle brackets.  
Example:

```java
List<String> names = new ArrayList<String>();
```

### <div style="text-align:center">**Generic Classes**</div>

When creating your own generic classes, the common syntax is to use `<T>` for a generic class to subsitute upon initialization.

Example:

```java
public class Crate<T> {
    private T contents;

    public void packCrate(T contents) {
        this.contents = contents;
    }
}
```

And when you initialize:

```java
Egg egg = new Egg();
Crate<Egg> crateOfEggs = new Crate<>();  // <-- Since 1.7, you don't need to name the second diamond
crateOfEggs.packCrate(Egg egg);
```

Generics can also have multiple variables:

```java
public class CrateWithSize<T, U> {
    private T contents;
    private U sizeType;
    //stuff...
}
```

### <div style="text-align:center">**Generic Interfaces**</div>

Interfaces can also have generics. See above, but picture an interface instead of a class.

### <div style="text-align:center">**Generic Methods**</div>

You can also use generics on methods, as seen the next example.  
This will return a Crate packed with `<T>`:

```java
public static <T> Crate<T> ship (T t) {
    System.out.println("Shipping " + t);
    return new Crate<T>();
}
```

### <div style="text-align:center">**Bounds**</div>

You can restrict what types are allowed in generics by using bounded wildcards.  
By default, generics can accept type `Object` (aka, EVERYTHING).

![3.1](./img/3.1.jpg)

So if you wanted to make a List that only worked with numbers, you could use the following code:

```java
List<? extends Number> list = new ArrayList<Integer>();
```

---

## 3.3 - Using Lists, Sets, Maps, and Queues

<u>**Java Collection**</u>: A group of objects contained in a single object.  
The 4 main interfaces in the **Java Collections Framework**:

1. <u>**List**</u>: Ordered collection of elements that allow duplicate entries.
2. <u>**Set**</u>: Collection that does not allow duplicate entries.
3. <u>**Queue**</u>: A collection that orders its elements in a specific order for processing.
4. <u>**Map**</u>: A collection that maps keys to values, with no duplicate keys allowed.

### <div style="text-align:center">Common Collections Methods</div>

<u>**add()**</u>: Inserts a new element and returns whether it was successful as a boolean value.

- Checking if false can be useful to determine if what you are trying to add is a duplicate value.

<u>**remove()**</u>: Removes a single matching value and returns whether it was successful as a boolean value.  
<u>**isEmpty()**</u>: Returns true if size of collection is zero.  
<u>**size()**</u>: Returns the size of the collection.  
<u>**clear()**</u>: Discards all elements in a collection. Returns nothing.  
<u>**contains(Object o)**</u>: Checks to see if collection contains `Ojbect o`, returns boolean value.

### <div style="text-align:center">Using the List Interface</div>

<u>**ArrayList**</u>: A resizable array. Use this when in doubt of what List to use. It's very common.  
<u>**LinkedList**</u>: A mix between a List and Queue.  
<u>**Vector**</u>: Old type (Java 1.2 days) that was pretty much replaced by ArrayList.  
<u>**Stack**</u>: Data structure where you add/remove from top of stack (FILO).

![3.2](./img/3.2.jpg)

Looping through a list example:

```java
for (String string: list) {
    System.out.println(string);
}
```

### <div style="text-align:center">Using the Set Interface</div>

<u>**HasSet**</u>: Stores it's elements in a hash table, using `hashCode()` to retrieve them.  
<u>**TreeSet**</u>: Stores elements in a sorted tree structure.

### <div style="text-align:center">Using the Queue Interface</div>

All queues are assumed to be FIFO (first-in, first-out).

<u>**LinkedList**</u>: LinkedList is also counted as a queue.  
<u>**ArrayDeque**</u>: A "pure" double-ended queue, more efficient than a LinkedList.

![3.3](./img/3.3.jpg)

<u>**E element()**</u>: Retrieves, but does not remove, the head of the queue represented by this deque.  
<u>**boolean offer(E e)**</u>: Returns true if the specified element was added at the end of this deque, else false.  
<u>**E poll()**</u>: Retrieves and removes the head of the queue represented by this deque.  
<u>**E pop()**</u>: Removes and returns the first element of this deque, or throws an exception if this deque is empty.

### <div style="text-align:center">Using the Map Interface</div>

<u>**HashMap**</u>: Stores the keys in a hash table.  
<u>**LinkedHashMap**</u>: Like HashMap, but retains order of keys.  
<u>**TreeMap**</u>: Stores the keys in a sorted tree structure.  
<u>**Hashtable**</u>: Like `Vector` it's old and replaced with HashMap. You still might see it in legacy code.

![3.4](./img/3.4.jpg)

---

## 3.4 - Comparator vs. Comparable

t