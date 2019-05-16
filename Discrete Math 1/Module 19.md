# Module 19 - Partial Order Relations

## 6.13 - Partial Order Relations

A relation $R$ on a set $A$ is a **Partial Order** if it is:

1. reflexive
2. anti-symmetric
3. transitive

Notation: $a\preceq{b}$ is used to express $aRb$ ($a$ has a relation to $b$)

The domain along with a partial order defined on it is called a **poset**

Two elements of a partially ordered set, $x$ and $y$ are **comparable** if ($x\preceq{y}$) or ($y\preceq{x}$).  
Otherwise they are **incomparable**.

**Total order** - A parial order in which every two elements in a domain are comparable.

**Minimal element** - an element x when there is no $y\neq{x}$ such that $y\preceq{x}$.

**Maximal element** - an element x when there is no $y\neq{x}$ such that $x\preceq{y}$.

[[Q: What does Transitive *really* mean?]]

---

## 6.14 - Partial orders and Hasse Diagrams

**Hasse diagram** - a way to depict a partial order on a finite set in which each element is represented by a label point. It shows precedence relationship by placing elements that are greater than others towards the top, similar to a "family tree".

For any $x$ and $y$ such that $x\neq{y}$:

- If $x\preceq{y}$, then make x appear lower in the diagram than y.
- If $x\preceq{y}$ and no such $z$ that $x\preceq{z}$ and $z\preceq{y}$, then draw a segment connecting $x$ and $y$.

More rules:

- If two points are connected with a line segment, then they are comparable.
- If two points are separated by other points connected by a path, it's comparable only if the line segments don't change direction (up to down or down to up).

---

## 6.15 - Strict order relations

**Partial order** uses $\preceq$, **Strict order** uses $\prec$.  
There is a strictness to the order of values.

A relation $R$ on a set $A$ is a **Strict Order** if it is:

1. Anti-reflexive
2. Transitive

---

## 6.16 - Strict order relations and directed acyclic graphs

**Directed Acyclic Graph (DAG)** is a directed graph that has no positive length cycles.

[[What is a positive length cycle? Review previous sections]]
