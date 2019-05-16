# Module 22 - Paths, Circuits, and Cycles

## 7.8 - Paths, cycles, and connectivity

**Walk** - A series of alternating vertices (v$_{n}$ to v$_{m}$, then v$_{m}$ to v$_{o}$) from one vertex to another.  
**Open walk** - The beginning and end vertex is not the same.  
**Closed walk** - The beginning and end vertex is the same.  
**Trail** - An open walk in which no edge occurs more than once.  
**Circuit** - A closed walk in which no edge occurs more than once.  
**Path** - A trail in which no vertex occurs more than once.  
**Cycle** - A circuit of length at least 1 in which no vertex occurs more than once, except the first and last vertices which are the same.

---

## 7.9 - Graph connectivity

**Connected vertices** - Two vertices are considered connected if there is a path between them on the graph.  
**K-Vertex-Connected graphs** - A graph is considered K# connected if $k-1$ vertices can be removed without the graph becoming disconnected.  
**K-Edge-Connected graphs** - A graph is considered K# connected if $k-1$ vertices can be removed without the graph becoming disconnected.  
(These are helpful when determining redundancy.)

NOTE: For a C-Connected Graph (circuit), removing two edges will make it disconnected. This applies for C$_{3}$ graphs or C$_{30000}$ graphs.
