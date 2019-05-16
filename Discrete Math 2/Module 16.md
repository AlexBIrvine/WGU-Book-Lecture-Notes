---
Date: 2019/04/28
Source: https://learn.zybooks.com/zybook/WGUC9602018/chapter/4/section/14
---

# Module 16 - Generating Permutations and Combinations

## 4.15 -  Generating permutations and combinations

**Lexicographic order** - Compares two tuples and how they differ, which one will be larger than the other.  
This follows the same rules as alphabetical order in grade school.  For (1,2,3,5) and (1,2,6,1), the second one is larger because where they differ (index 3, or 3 & 6) it's larger.  
This only works for *sequences* and *tuples* where the order matters. 

**Algorithm to generate permutations in lexicographic order**
```
GenLexPermutations(n)

Initialize P = (1, 2, …, n - 1, n)
Output P
While P ≠ (n, n - 1, …, 2, 1),
    P = NextPerm(P)
    Output P
```

(4.15.4: Finding the next permutation in lexicographic order.  <- is very helpful)

---

## 4.16 - Generating r-subsets of a set

Where the order doesn't matter, you first sort the set in increasing order to compare them.  
So {3,2,4} > {5,1,3} because sorted they become {2,3,4} > {1,3,5}  

**Algorithm to generate r-subsets in lexicographic order**
```
GenLexSubsets(r, n)

Initialize S = {1, 2, …, r-1, r}
Output P
While S ≠ {n-r+1, …, n-1, n},
    S = NextSubset(n, S)
    Output S
```
