# Module 5 - Prime Factorization, GCD, and Euclid's Algorithm

## 2.7 - Prime Factorizations

**Prime Number** - A number n is prime if it's only factors are 1 and n.  

**Prime Factorization** - Every integer greater than 1 can be expressed as a product of prime numbers, which is it's prime factorization.  

**Non-Decreasing Sequence** - each number is equal to or greater than the one that came before.  

Good Example: 1, 1, 2, 3, 17  
Bad Example:  1, 1, 3, 2, 17  

**Multiplicity of a Prime Factor** - The number of times a number p appears in a product of primes.  This is represented as an exponent.  
For 120, the product of primes in a non-decreasing sequence is $2·2·2·3·5$.  This can be written as $2^3·3·5$. 


### **ONE IS NOT A PRIME NUMBER**

---

## 2.8 - Greatest common division and least common multiple

**Greatest Common Divisor (GCD)** - For non-zero integers x & y, the largest integer that factors into both x & y.  

**Least Common Multiple (LCM)** - For non-zero integers x & y, the smallest integer that is an integer multiple of both x & y.  

To find the greatest common divisor between two numbers, first find the prime factorization of both.  If for example you were trying to find the GCD of 147 and 315, it's prime factorizations are:  
$147 = 3 * 7^2$  
$315 = 3^2 * 5 * 7$  

To compare both, you can add $5^0$ to the list of 147's prime factorization.  

From here, take the minimum value of the exponents for each prime number, then find the product of that.  So...  

GCD(147, 315) = $3^1 * 5^0 * 7^1 = 3 * 7 = 21$

To find the least common multiple, take the same approach above but use the maximum value for each exponent.  

LCD(147, 315) = $3^2 * 5^1 * 7^2 = 9 * 5 * 49 = 2205$

---

## 2.9 - Factoring and primality testing

Chances of a number x is a prime number is: $\frac{1}{\ln{x}}$

**A "better" brute force methond for finding prime number:**
```
Input: Integer N greater than 1.
Output: "Composite" if composite, else "Prime".

For x = 2 to  
      If x evenly divides N,
            Return( "Composite" )
End-for

Return( "Prime" )
```


---

## 2.10 - Euclidean algorithm

**Euclid's algorithm for finding the greatest common divisor**
```
Input: Two positive integers, x and y.
Output: gcd(x, y).

If ( y < x )
      Swap x and y.
r = y mod x.

While ( r ≠ 0 )
      y := x
      x := r.
      r := y mod x.
End-while

Return( x )
```

---

