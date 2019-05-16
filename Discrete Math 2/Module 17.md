---
Date: 2019/04/30
Source: https://learn.zybooks.com/zybook/WGUC9602018/chapter/4/section/17
---

# Module 17 - Advanced Counting Techniques

## 4.18 - Inclusion-exclusion principle

**inclusion-exclusion principle** - When counting two sets that overlap (red playing cards & face cards) you will need to use the following formula to not count the intersection twice:

$|A \cup B| = |A| + |B| - |A \cap B|$

**inclusion-exclusion principle with 3 sets** -

$|A \cup B \cup C| = |A| + |B| + |C| - |A \cap B| - |B \cap C| - |A \cap C| + |A \cap B \cap C|$

---

## 4.19 - Binomial coefficients and combinatorial identities

**combinatorial identity**:  
$\binom{n}{k} \equiv \binom{n}{n-k}$

**The Binomial Theorem**:  
$$(a+b)^n = \sum_{k=0}^{n} \binom{n}{k} a^{n-k}b^k$$

![17.1](./Img/17.1.JPG)

**Pascal's Triangle**  
Construct a triangle with binomials $\binom{n}{k}$ where $n$ is the number of rows from the top (0 being the tip) and $k$ being the index (or column) in row $n$.  
To calculate each rows value, the outside values are 1, and the inside values are the sum of the two numbers above it.

![17.2](./Img/17.2.JPG)

---

## 4.20 - The pigeonhole principle

**Pigeonhole Principle** - if n+1 pigeons are placed in n boxes, then there must be at least one box with more than one pigeon.

In other words:

- If you have 3 colors of socks. After 3 socks are selected, there might not be a pairAfter the next sock is selected, it will make a pair.
- Among a group of 400 people, there are at least two who have the same birthday.

![17.3](./Img/17.3.JPG)

**Generalized pigeonhole principle**

```
Suppose that a function maps a set of n elements to a target set with k elements, where n and k are positive integers.
In order to guarantee that there is an element y in the target to which f maps at least b items,
then n must be at least k(b - 1) + 1.
```

This works for situations where you are filling in a list evenly. Say you are creating two basketball teams and want to know how many people you have to pick until at least one team has someone on the bench. That would be from a set N (students in gym class) going to set K (basketball teams), where b is a benched player (or 6 people on a team).  
$k(b-1)+1$  
or $2(6-1)+1 = 11$  
So the 11th player pick is guaranteed to be placed on the bench.
