# Module 2 - Analyzing Algorithms

## 1.9 - Computational complexity

**Algorithm Complexity** - The study of the efficacy of algorithms that gives us a framework to compare algorithms.  
**Time Complexity** - The ammount of time needed to perform the algorithm.  
**Space Complexity** - The ammount of space needed to perform the algorithm.  

Input size affects algorithm efficiency.  

---

## 1.10 - Evaluating algorithm complexity

**Atomic Operations** - Operators that cannot be further split (+, -, *, >, !=, etc.,)

Counting atomic operations example:  
```
Max: = 0
For i: =1 to n
    If (a[i] > Max), Max: = a[i]
End-for
```

Number of atomic operations:  
1. Assigning a value to a variable
2. Looking up the value of a particular element in a sequence
3. Comparing two values
4. Incrementing a value (and/or arithmetic operations such as addition and multiplication)

--- 

## 1.11 - Worst-case analysis

(compute the worst case scenario of a particular algorithm to make informed decisions) 