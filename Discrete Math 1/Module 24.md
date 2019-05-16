# Module 24 - Tree Traversals and Spanning Trees

## 7.14 - Tree traversals

**pre-order traversal** - vertices are visited before their descendants.  
Example tree (in outline form):  
Order of traversal = A, B, C, D, E, F, G

- A
  - B
    - C
    - D
  - E
  - F
    - G

**post-order traversal** - leaves are visited first, then their parents.  
Example tree (in outline form):  
Order of traversal = D, C, B, G, F, E, A

- A
  - B
    - C
    - D
  - E
  - F
    - G

---

## 7.15 - Spanning trees- Breadth-first and depth-first search

**Spanning Tree** - A path in a graph that will connect to every vertex without taking alternate route to them.

**Breadth-First Search (BFS)**

```
Breadth-first-search

Input: An undirected, connected graph G. A start vertex v1
Output: T, a breadth-first search tree.

Add v1 to T.
Add v1 to the back of the list.

While the list is not empty:
      Remove vertex v from the front of the list.
      For each neighbor w of v that is not already in T:
            Add w and {w, v} to T.
            Insert w at the back of the list.
      End-for
End-while
```

**Depth-First Search (DFS)**

```
Input: An undirected, connected graph G. A start vertex v1
Output: T, a depth-first search tree.

Add v1 to T. visit(v1)
visit(v)

For every neighbor w of v:
      If w is not already in T
            Add w and {w, v} to T.
            visit(w);
      End-if
End-for
```

---

## 7.16 - Minimum spanning trees

**Weighted graph** - A number is assigned to every edge of a graph. The _sum_ of the graph/subgraph is the sum of all the weights.

**Minimum Spanning Tree (MST)** - A spanning tree of a graph with the lowest weight.

**Prim's algorithm for minimum spanning tree**

```
Input: An undirected, connected, weighted graph G.
Output: T, a minimum spanning tree for G.

T := ∅.
Pick any vertex in G and add it to T.

For j = 1 to n-1
      Let C be the set of edges with one endpoint inside T and one endpoint outside T.
      Let e be a minimum weight edge in C.
      Add e to T.
      Add the endpoint of e not already in T to T.
End-for
```
