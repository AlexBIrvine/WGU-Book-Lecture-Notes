---
Date: 2019/05/01
Source: https://learn.zybooks.com/zybook/WGUC9602018/chapter/5/section/2
---

# Module 18 - Introduction to Discrete Probability

## 5.3 - Introduction to discrete probability

**Outcome** - A single possible output.  
**Sample Space** - Set of all possbile outcomes.  
**Event** - Subset of the Sample Space.  
**Discrete probability** - Experiments in which the sample space is a finite or countably infinite set.  
**countably infinite** - one-to-one correspondence between the elements of the set and the integers.

---

## 5.4 - Probability of an event

$P(E) = \frac{|E|}{|S|}$ where E is how many times the event can come up, and S is the entire sample size.  
Example, getting a 1 on a d6 is 1/6.  
Getting a 6 on a loaded d6, where 6 is twice as likely to come up is 2/7.

---

## 5.5 - Inclusion-exclusion rule

**Mutually exclusiive events** - Two or more events that cannot coexist.  
Example: in a sample space of 5 coin flips, the first three flips are heads and the last three flips are tails.  
Both cannot exist at the same time.

If two events are not mutually exclusive, the probability of the union of events can be determined by a version of the **Inclusion-Exclusion principle**:

$$p(E_1 \cup E_2) = p(E_1) + p(E_2) - p(E_1 \cap E_2)$$

---

## 5.6 - Complement rule

$p(\overline{E}) = 1 - p(E)$

Because it's sometimes easier to find out the opposite and subtract that from the total than it is to find out the event itself.
