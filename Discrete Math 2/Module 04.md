# Module 4 - Divisibility and Modular Arithmetic

## 2.3 - The division algorithm

**Number Theory** - Branch of mathematics concerned with integers.  

**Integer Division** - Division with remainder.  

```(pseudo code)
Input: Integers n and d > 0.
Output: q = n div d, and r = n mod d.

Case 1: n ≥ 0.'

q := 0
r := n
While ( r ≥ d )
      q := q + 1
      r := r - d
End-While
```

---

## 2.4 - Modular arithmetic and multiplication

(this section is stupid and can be summed up as "do math before you take mod anything)

example:  $6 + 8 \mod 4 \equiv 14 \mod 4$

--- 

## 2.5 - Congruence modulo n

**congruence** - meaning "same measure".  Examples are $400\degree \equiv 40\degree$ on unit circle, and 13:00 $\equiv$ 1:00 PM for time.  

In modular arithmetic, the results of two mod operations are considered congruent if the result is the same.  
So $13 \mod 4 \equiv 29 \mod 4$

For very large numbers ( example: $(43^{17} + 32 * 139) \mod 7$ ) you can break them down thanks to congruency.  
This means the above can be simplified as $43 \mod 7 + 32 \mod 7 * 139 \mod 7$.  

