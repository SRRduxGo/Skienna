# [Graph Data Structures](https://youtu.be/OiXxhDrFruw?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b)

## Graphs

> **A Graph `G = (V,E)` is defined by set of `vertices` `V`, and set of edges `E` consisting of `ordered` and un-ordered pairs of `Vertices` from `V`**
>
> Graph algorithms are `Subtle`
> Examples: Road Network, Electronic Circuits
> `Network ≈ Garph`
> #Design Graphs not Algorithms#

## Flavours of Graphs

- **The first step in any graph problem is determining which flavour of Graph you are dealing with**
- **Learning to `talk the talk` is an important part of walking the walk**
- **The `flavour` of `Graph` has a big impact on `which Algorithms` are appropriate and efficient**

## Directed vs. Undirected Graphs

- **A graph `G = (V, E)` is undirected if edge `(x,y) ∈ E` implies that `(y,x)` is also in `E`**
- Example - Program call graph, flow from subroutine to subroutine
- **Take a problem and reduce it to a Graph problem**

## Weighted vs. Unweighted Graphs

- **In `weighted` graphs, `each edge (or vertex)` of `G` is assigned a `numerical value`, or `weight`**
- **In `unweighted` graphs, there is no `COST` distinction between various `edges and vertices`**
- ****

## Simple vs. Non-Simple Graphs

- **a `self-loop` is an edge `(x,x)` involving only one vertex**
- **an edge `(x,y)` is a multi-edge if it occurs more than once in the Graph**
- **`ANY GRAPH` which avoids these structures is called `SIMPLE`**

## Sparse vs. Dense Graphs

- **Graphs are `sparse` when only a `small fraction` of the possible number of `vertex pairs` actually have edges defined between them**
- **`Dense` Graphs have a `Quadratic` no. of `Edges` defined between them while `Sparse` Graphs are `Linear` in size**
- ****

## Cyclic vs. Acyclic Graphs

- **A `Acyclic` graph doesn't contain any `cycles` (even loops 0O)! )**
  - Trees are connected `Acyclic Undirected` graphs
- **`Directed Acyclic` graphs are called DAGs**

## Labeled vs. Unlabeled Graphs

- **In `labeled` graphs, each vertex is assigned a Unique name or identifier to distinguish it from all other vertices**
- **An important Graph problem is `isomorphism testing`, determining whether the `topological structure` of two Graphs are in fact identical if we ignore any labels**

## Data Structures for Graphs: Adjacency Matrix

- **Two main Data structures used to represent Graphs**
  - _We assume the Graph G = (V,E) contain `N` `vertices` and `M` `edges`_
- **We can represent `G` using an `n*n` matrix `M`**
  - _Element `M[i, j]` has value `1` if `(i,j)` is an `Edge` of `G` and `0` if it is `NOT`_
  - _This representation may take `excessive space` for `Graphs` with many `vertices` and `relatively` fewer `edges`_

## Adjacency Lists

- **An `adjacency list` consists of a `(N * 1)` `Array` of pointers. Accessing element in an Array using the `Index` ≈ `O(1)` time**
- **`i`th element points to a `Linked-List` of the edges incident on the vertex `i`**
- **To test if `edge(i,j)` is in the Graph, we search the `i`th linked-list for `j`**
  - **Which takes `O(d`<sub>`i`</sub>`)`, where `d`<sub>`i`</sub> is the degree of the `i`th Vertex**
  - _Note that `d`<sub>`i`</sub> can be much less than `n`when the Graph is `Sparse`_
  - _If necessary, the `two copies` of `each edge` can be `linked by a pointer` to facilitate deletions_

## Trade offs between Adjacency List and Adjacency Matrices

- _Faster test if (x,y) exists? - Matrix representation_
- _Faster to find Vertex degree? - List representation_
- _Less Memory on Sparse Graphs? - List(m-edges + n-vertices)|winner| vs (nˆ2)_
- _Less Memory on Dense Graphs? - Matrices(small win)_
- _Edge Insertion and Deletion? - Matrices- O(1)_
- _Faster to traverse the Graph? - Lists( m + n) vs nˆ2_
- _Better for most problems? Lists_
