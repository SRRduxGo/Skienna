# BFS Musings

> [MIT](https://www.youtube.com/watch?v=s-CYnVz-uh4)

>## Graph Search

- `explore` a graph
- Graph = `(V,E)`

> Note: V = Set of vertices / E = Set of edges

- `e ∈ E` ⤇ `{v,w}` unordered pairs `un-directed graph`
- `e ∈ E` ⤇ `{v,w}` ordered pairs `directed graph`

>## Application

- _Web Crawling_
- _Network Broadcast_  
- _Garbage Collection_
- _Model checking_


>## How to represent a Graph for an Algorithm

- Representing an edge list is a **poor** representation to search on
- Translating or Representing the problem universe as a Graph is the key
- _Diameter of a Graph ??_

>## Graph representation

- Adjacency list Adj
  - Array of size |V| :`number of vertices`
  - Each element is a pointer to a Linked-List
  - Array is indexed by a vertex `u ∈ V`
    - > It means : for each vertext  `u ∈ V`, `Adj[u]`
    - > `Adj[u]` stores its `Neighbours` ⤇ vertices which can be reached in one step
      - >_`Neighbours`_ :: {v ∈ V | (u,v) ∈ E }
    - _space required to store this Graph Representation_ `ϴ(|v| + |E|)`

>## Breadth-First Search

- Visit all the nodes reachable from the given node `s ∈ V`
- We want to achieve `ϴ(|v| + |E|)` time
- Look at the Nodes reachable in **_`Zero Moves`_** - `s`, then **_`One move`_** `Adj[u]`, the **_`Two moves`_**  and so on
- Careful to avoid duplicates
- **Assign levels to nodes ⤇ An indicator of shortest paths**
- > Create **Frontier** :`[step 1 edges from the origin]` + **Next** `[step 1 edges from the Frontier ]` ⤇ **Next** becomes the **_`new`_** **Frontier** and fresh **Next** is calulated using the **_`new`_** **Frontier**




