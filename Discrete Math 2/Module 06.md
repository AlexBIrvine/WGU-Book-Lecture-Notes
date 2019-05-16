# Module 6 - Number Representation in Other Bases

## 2.14 - Number representation- Decimal and binary numbers

For a number with base $b$, represented like (1234)$_b$ it can be rewritten (1*$b^3$ + 2*$b^2$ + 3*$b^1$ + 4*$b^0$), assuming the base has enough digits to accommodate that 4.

---

## 2.15 - Number representation- Hexadecimal numbers

Hexadecimal is a base 16 numbering system with letters up to F to represent 15.

Hexadecimal goes into binary very well, each hex number being represented by 4 binary numbers (0000 - 1111).

| Hex | Decimal | Binary |
| :-: | :-----: | :----: |
|  0  |    0    |  0000  |
|  1  |    1    |  0001  |
|  2  |    2    |  0010  |
|  3  |    3    |  0011  |
|  4  |    4    |  0100  |
|  5  |    5    |  0101  |
|  6  |    6    |  0110  |
|  7  |    7    |  0111  |
|  8  |    8    |  1000  |
|  9  |    9    |  1001  |
|  A  |   10    |  1010  |
|  B  |   11    |  1011  |
|  C  |   12    |  1100  |
|  D  |   13    |  1101  |
|  E  |   14    |  1110  |
|  F  |   15    |  1111  |

---

## 2.16 - Base b expansion

**Algorithm to find the base b expansion for a positive integer**

```
Input: Integers n and b. b > 1 and n ≥ 1.
Output: Base b expansion of n. Base b digits are output in reverse order.

x := n
while ( x > 0 )
      Output( x mod b )
      x := x div b
End-while
```

**The number of digits required to represent a number** - Can be found with the formula: $\log_b(n+1)$  
Example: How many digits are required to express the base 7 expansion of 2401? $\log_7(2402)$
