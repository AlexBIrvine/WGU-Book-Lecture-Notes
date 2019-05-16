# Module 21 - Undirected Finite Graphs and Diagrams

## 7.3 - Introduction to undirected graphs

**Undirected Graphs** - Graphs that do not use vertices (arrows) between nodes.  They are good at showing symmetric relations, as in siblings in a family vs parent/child relationships.  

*Denoted:* A = { {$a$, $b$}, {$b$, $c$} }  
Note that since the order in a set does not matter, we can use the curly braces inside as well.  This is what separates this notation from directed graphs.  

### Definitions
**Adjacent** - When there is an edge (line) between two vertices.  
**Endpoints** - $b$ and $c$ are *endpoints* of *edge* {$b$, $c$}.  
**Incident** - The edge {$b$, $c$} is an *incident* to vertices $b$ and $c$.  
**Neighbor** - Two vertices are neighbors if there is a line (edge) between them.  
**Degree** - The degree of a vertex is the # of neighbors.  
**Total Degree** - Sum of the degrees of all vertices.  
**Regular Graph** - A graph where all vertices have the same degree.  Example: 3-regular graph has each vertex with a degree of 3.  


---

## 7.4 - Graph theory and common graphs

The total degree can be found easily by counting the number of edges (lines connecting dots) and multiplying that number by 2.  

**Complete Graph** ( K$_{n}$) - Looks like a star network diagram, it has an edge between every pair of vertices.  
**Cycle** (C$_{n}$) - Looks like a ring network diagram.  Connects $n$ vertices in a ring.  
**N-dimensional Hypercube** (Q$_{n}$) - This has 2$^{n}$ vertices.  
**K$_{n,m}$ Graph** - This has $n$+$m$ vertices.  The vertices are divided into two sets: one with m vertices and one set with n vertices.  
There are no edges between vertices in the same set, but there is an edge between every vertex in one set and every vertex in the other set.  

---

## 7.5 - Undirected graph representations

Since computers don't view data with graphs like humans do, they need a different way to input graphs.  There are two common ways, *Adjacency list representation* and *Matrix representation*  

**Adjacency list representation** - Constructs a lists of lists.  First list is each vertex in the graph, and that will have a list of all neighbors.  
**Matrix representation** - Takes a graph of $n$ vertices, and creates a square binary matrix of $n$ rows/columns.  Value of 1 is present in $n$ row/column & $m$ column/row if there is an edge between two vertices.  

---

## 7.6 - Undirected graph representations

**Isomorphic** - Two graphs that have the same "shape" (structure of edges) but different placements of vertices are not identical, but *isomorphic*.  
**Degree Sequence** - A list of all the degrees of all the vertices in a graph in a non-increasing order.  
(*Degree sequence* is converserved under *isomorphism*)  

