---
Date: 2019/05/05
Source: https://learn.zybooks.com/zybook/WGUC9602018/chapter/6/section/2
---

# Module 21 - Deterministic Finite State Machine

## 6.3 - Theory of computation

**Computation** - Any type of calculation that follows steps that provide a solution to a problem.

**4 Major Families of Automata**

1. **Finite State Machine** - Every bit exists as either a 0 or 1, and a finite possibility of inputs exist.
2. **Pushdown Automaton** - Uses a stack/collection that collects elements.
3. **Linear-bounded Automation** - Two end markers with input in between.
4. **Turing Machine** - A finite state machine with infinite storage.

**Grammar** - A set of rules for generating strings.

---

## 6.4 - Deterministic finite state automata (DFA)

A deterministic finite state machine is a machine who's outcomes are predetermined and dependent on the input.  
For example, a subway turnstile. It starts locked, and accepts either a push or a coin. If it gets a coin, it unlocks (and therefore can be pushed).  
If it's pushed while unlocked, it turns then locks.

DFA components:
**Alphabet** - The finite amount of input strings.  
**Transistion Function** - The set of rules that determine the output. Based on current state and next input string.  
**Start State** - The state of which processing strings begins.

![21.1](./Img/21.1.JPG)

---

## 6.5 - DFA state diagrams

(Below is a visualization of the DFA state)

![21.2](./Img/21.2.JPG)

---

## 6.6 - DFA state transition tables

A table can be used to represent the transition between states.  
The columns will be the input, the rows being the current state.  
The cells will be the output (given the current state and input)

|              |   COIN   |  PUSH  |
| :----------: | :------: | :----: |
|  **LOCKED**  | UNLOCKED | LOCKED |
| **UNLOCKED** | UNLOCKED | LOCKED |

---

## 6.7 - DFA analyzing transition rules

(Examples & exercises of the three sections above)

---

## 6.8 - DFA evaluating outcomes

Some finite state machines can have "accepting" values, meaning that the output is "true" if it ends in a certain state.  
On a diagram, this is represented by a double circle around the state.
