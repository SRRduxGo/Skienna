# [Heap-Sort / Priority Queues _(mains)_](https://youtu.be/yLvp-pB8mak?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b)

## oO/

> **Food For Thought - Two sets - whether they are Dis-Joint or total intersections? a set with n elements and a set with m elements. And n >> m**

<hr/>

### _Selection Sort - AFTERMATH :/_

> - **_`n log n` => `sort and find`_** the larger of the two and search the using the elements from the smaller set on the sorted larger set **_( `n log n [sort time] + m log n [search time]`)_**
> - **_if we use a HashTable - `O(m [hash table build time] . O(n) [search time]) ≈ O(nˆ2)`_**
> - _optionally - `intersection = concatenate + sort + sweep` ..still it is `O(N log(N))`_

<hr/>

> **why deletion in a Binary tree takes `n log(n)` time - worst case? 0O/ think! and find**

- _Using `Array` or `unsorted linked-lists` as Data structure, Operation A will take `O(n)` time and B takes `O(1)` time, for `O(nˆ2)` `selection sort`_
- _But by using Balanced-BST OR **HEAPS**, both of these operations can be done within `log(n)` time and thus making `Selection Sort` an `O(n Log n)` algorithm_

> **What is the lesson of Selection Sort?**
> Change of data-structure can give you better trade-off for the same Algorithm

## Heap

### what is a Heap oO/

- A `Binary Heap` is defined to be a `binary tree` **`(NOT SEARCH)`** with a key in each Node such that -
  - 1 _All `Leaves` are on, at most, `two adjacent levels`_
  - 2 _All `Leaves` on the lowest level occur to the `left`, and all levels except the lowest(and the Last but one) level are `completely filled`_
  - 3 _The `key` in the Root is ***`≤`*** all its children, and the left and the right subtree are again `Binary Heaps`_
  - _1 and 2 define the shape of the tree and 3 defines the labeling_
  - ***SMALLEST ELEMENT IS AT THE ROOT***
  - Height of the tree Heap is going to be **exactly `Log N`**

#### Heap Trivia

- Heaps maintain a Partial Order
- which is weaker than the Sorted Order - so it can be efficient to maintain - easy to insert stuff
- Yet stronger than Random Order - Helps quickly identifying the sorted Order

  > Heap is not designed for efficient lookups - Min and Max [Heaps](https://youtu.be/sU0r4AXgRyk?list=PLOtl7M3yp-DX32N0fVIyvn7ipWKNGmwpp&t=3967)

### Array Based Heaps

- We can store a Tree as an Array of Keys, using the position of the keys to IMPLICITLY satisfy the role of the pointers
  - The `Left-Child` of a node at position `k` sits in the position `2k` and `Right-Child` in position `2k+1`
  - `Parent` of `k` sits at position `[k/2]`
- _Lower flexibility in moving `Node` positions and but less Memory Usage due to `Pointer-less` implementation_

### Implicit Representation of a Binary Tree oO/

- _It is only efficient if the Tree is `Sparse` - Number of nodes in the tree `N` < `2ˆh`, where `h` is the height of the Tree_
- ***All the `missing Nodes` will `take up space` in the Implicit Representation***
- `Not` well suited for  **`ARBITRARY modifications`  (SINCE: NOT POINTER BASED)** due to the  `Implicit - Rigidity` in the data Structure
- _Worst case scenario for a Sparse Tree - taking up `O(2ˆn)` space for `n` nodes - Imagine a tree with only a right Arm_ ***(oO/.. think!)***

> Selection Sort : Get an array from Binary Heap following Selection Sort Algorithm - `O(N log N)`

<hr/>

> Same logic can be used to BUILD A HEAP - Bubble Down / Heapify:
>
> - _Given Two Heaps `h1` & `h2`_
> - _A Fresh element `e`_
> - _make `e` the root and `h1`nad `h2` the new children and `bubble down`_
> [BUBBLE DOWN](https://youtu.be/yLvp-pB8mak?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=4205)

### BACK TO BINARY HEAP

- `Inserting` an element in a `Binary Heap` - following all the rules - worst case `Log N` time - moving the newly added node up the ladder **(oO/ think!)**
- Faster Way to build a `Heap`
  - _Using Heapify to construct Heap_
  - _An isolated element forms a Heap of Size 1_
  - __
  
  ```js
    HeapSort(A)
        Build-Heap(A) // n log n
        for i = n to 1 do  // n (log n)
            SWAP(A[1],A[i])
            n = n - 1
            Heapify(A,1)
            // total = `2n log n` ≈ `n log n`
  ```
  
  - _Exchanging the maximum element with the last element and calling `Heapify` repeatedly gives `O(n log n)` Algorithm_

### Heap Construction

- Heaps can be constructed incrementally
- _insert the new element in the `left-most` open spot_
- _if the new element is greater than its parent - `swap` their places and `RECURSE` this check till heap becomes `HAPPY` and **satisfies all three rules (MIN HEAP)**_
- **Since All (but the last level) is always filled, the height `h` of an `n` element heap is `BOUNDED` because**
  - _`∑(i = 1 to h) 2ˆi = 2ˆ(h + 1) - 1 ≥ n`_ **( _TODO_: ..HOW oO/. - have to figure out ?..)**
  - _So `h ≈ log n`_
  > _Doing `n` such insertions really takes `O(n log n)` time, because `last n/2` insertions require `O(log n)` time `EACH`_

<hr/>

> ***Heap-Sort is nothing but Selection-Sort with a different `Data Structure` called a `Heap`***

## Priority Queues

- _Priority Queues are Data Structures which provide extra flexibility over sorting_
- _Abstract Data Type which allows you to `Repeatedly` find a MIN and DO INSERTIONS_

### Priority Queue Operations

- _`INSERT(Q,x)`: Given an Item `x` with the key `k`, insert it into the `Priority Queue` - `Q`_
- _`FIND-MINIMUM(Q)` or `FIND-MAXIMUM(Q)`: Return a pointer to the item whose key value is smaller (larger) than any other key in the priority queue `Q`_
- _`DELETE-MINIMUM(Q)` or `DELETE-MAXIMUM(Q)` : Remove an item from the Queue whose key is Minimum (Maximum)_

### Implementation

- _A Heap or Balanced-BT (NOT SEARCH) can be used - each operation would cost `O(log N)` time_

### Use Case

- _Dating Applications - [;D](https://youtu.be/yLvp-pB8mak?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=4444)_
- _Discrete Event Simulation - Priority used to maintain who goes next_
- _The Stack and the Queue Order - special cases of Ordering - In real life tasks based on Priority cut the already existing line_
- _`Greedy Algorithms`:_
  - _We always pick the next thing which locally maximizes our score_
  - _By placing all the things in a Priority Queue_
  - _Pulling them off in-order - Improves performance over Linear Search OR Sorting - particularly if the weights change_

> **PRIORITY QUEUE is BEST for Situations where PRIORITY of ITEMS in QUESTION keeps changing**

<hr/>

> [ANIMATION](https://upload.wikimedia.org/wikipedia/commons/4/4d/Heapsort-example.gif)
