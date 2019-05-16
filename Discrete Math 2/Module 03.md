# Module 3 - Big-O Estimates

## 1.13 - Asymptotic growth

**Asymptotic complexity** -  Describes the behavior of the complexity function as n grows.

To find asymptotic complexity, remove all constants and focus in on the factor that grows the fastest.  

Examples:  
1. $f(n) = 32n + 50$ has an asymtotic complexity of $n$, since we ignore 50 and 32.  
2. $f(n) = 64n^2 + 32n + 50$ has an asymtotic complexity of $n^2$, since we ignore constants and the slower growing $n$. 

| # of loops | Asymtotic Complexity |
| :--------: | :------------------: |
|     0      |          1           |
|     1      |         $n$          |
|     2      |        $n^2$         |
|     x      |        $n^x$         |

---

## 1.14 Lesson: Algorithms and big-O


**Big-O notation( $O(n)$ )** - The upper bound for the asymptotic complexity.  
**Big-Omega notation( $\Omega(n)$ )** - The lower bound for the asymptotic complexity.  
**Big-Theta notation( $\Theta(n)$ )** - [Somewhere in the middle of asymptotic complexity?].

$\Omega( f(n) ) \leq \Theta( f(n) ) \leq O( f(n) )$
