---
Date: 2019/04/24
Source: https://learn.zybooks.com/zybook/WGUC9602018/chapter/4/section/2
---

# Module 13 - Counting by Bijections and Products of Sets

## 4.3 - Sum and product rules

**Product Rule** - For a series of finite sets, the product (or the cardinality of) the set is |set| \* |set|...  
So if you have a meal that is made of 1 drink, 1 dish, 1 desert, and you have 3 options for each, there will be this many possible chocies:  
$|drink| * |dish| * |desert| = 3 * 3 * 3 = 27$ possible choices.

To **count strings** with this rule, you first need to know how many possible choices there are for each "letter'.  
For example, to count how many possible choices there are for a 5 letter "word" of binary (so $\{0,1\}$ ) you would do = $\{0,1\}^5$ or $2^5 = 32$.  
For the possible amount of words using the english alphabet for length $n$ you would have $26^n$

**Sum Rule** - For when there are multiple choices but only one selection is made.  
So if you have a meal with the choice of a hot drink (coffee or tea) or a cold drink (coke, milkshake or water) and the customer only wants one drink, you would do:  
$|$cold drinks$| + |$hot drinks$| = 2 + 3 = 5$  
To use this, all sets must be disjoint of each other (or in other words, an element is not in multiple sets. A drink can't be both hot and cold in this example)

An example that threw me off is:

**Q: How many binary strings of length 5 or 6 start with a 1?**

To answer this, find out how many strings exist that start with a 1 that are length of 5 ($2^4 = 16$)  
Next, find out how many strings exist that start with a 1 that are length of 6 ($2^5 = 32$)  
Add them together. The answer is 48.

---

## 4.4 - Bijection rule

If a set has a well defined inverse ( so $f(s) = t$, if and only if $g(t) = s$ ), then the two sets have the same cardinality. In other words, if the sets are a bijection of each other, then they have the same cardinality.

The **k-to-1 rule** states that if there is a k-to-1 difference between sets $A$ and $B$, then $|B| = |A|/k$.  
In simple terms, a pile of shoes typically has a 2-to-1 ratio between humans (2 feet, 2 shoes) so |humans| = |shoes|/2.

---

## 4.5 - The generalized product rule

The set can "change size" when using the product/sum rules.  
If you have a set of 10 racers and want to know the different possibilities of podium winners, then you would do:

$|10| * |9| * |8|$ since someone cannot win two different medals.
