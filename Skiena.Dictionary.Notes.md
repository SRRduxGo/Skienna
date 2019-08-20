# Dictionary

[Skiena](https://www.youtube.com/watch?v=2YcHOsrPLKE&list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&index=5)

## Dictionary / Dynamic set operations

- Perhaps the most important class of Data-Structures | maintain set of items, indexed by keys
  - Search **_`(S,k)`_** - A query that,given a set **_`S`_** and a key value **_`k`_**, returns a pointer **_`x`_** to
    an element in **_`S`_** such that **_`key[x] = k`_**
  - Insert **_`(S,x)`_** - A modifying operation that augments the set **_`S`_** with the element **_`x`_**
  - Delete **_`(S,x)`_** - Given a pointer **_`x`_** to an element in the Set **_`S`_**, remove **_`x`_** from **_`S`_**
  - Min**_`(S)`_**, Max **_`(S)`_** - Returns the element of the totally ordered set **_`S`_** which has the smallest (largest) key
  - Next **_`(S,x)`_**, Previous **_`(S,x)`_** - Given an element **_`x`_** whose key is from the
    totally ordered set **_`S`_**, returns the next largest(smallest) element in **_`S`_**, or `NIL` if x is the maximum(minimum) element

## Problem of the Day

- when a dictionary is implemented as the following Data structures, what will be the
  **_Asymptotic Worst Case Running times for each of the dictionary operations_**
  - Singly-Linked unsorted list
  - Doubly-Linked unsorted list
  - Singly-Linked Sorted
  - Doubly-Linked Sorted

### Analysis

- SL UN`ORD
  - > => Search O(n), Insert O(1), Delete O(n) OR O(1) (unsorted), Next O(n), Previous O(n), Min O(n) OR O(1) if keeping a pointer at the min / max element, Max O(n)
- DL UN`ORD
  - > => Search O(n), Insert O(1), Delete O(1), Next O(n), Previous O(n), Min O(n), Max O(n)
- SL`ORD
  - > => Search O(n), Insert O(n) {OPERATION BLOCK: check current position in-order then insert else move forward},
    > Delete O (n), Next O(1), Previous O(n), Min O(1), Max O(1) { if maintain a tail pointer }
- DL`ORD
  - _Has to be revisited_

> **_which is the best implementation ?_**

- _`Looking at the analysis - Doubly Linked Lists`_

### `BINARY SEARCH TREE IMPLEMENTATION OF A DICTIONARY ? ( ..oO/<< Seriously now!.. )`

- _It supports all SIX Dictionary operations_
  - _BINARY Tree is a `rooted tree` where each node `at most` can have `two children` : LEFT or RIGHT : Child_
- Gives good trade-off between what we analysed in SL and DL implementations
- _Binary `Search` tree labels each node as `X` in such a way_
  - _All nodes in the `left subtree` of `X` have keys `K` such that `{k ∈ K }` < `X`_
  - _All nodes in the `right subtree` of `X` have keys `K'` such that `{k' ∈ K' }` > `X`_
- _**For a BS-Tree order of the keys matter**_
- _There is `only one way to label` a node in a BS-Tree_
- _KNOWING THE STRUCTURE OF A BS-TREE AND ORDER OF THE KEYS ONE CAN ASCERTAIN THE LABEL OF THE ROOT NODE [SKIENA](https://youtu.be/2YcHOsrPLKE?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=2833)_
- **Same reasoning can be used to figure out - by looking at the physical structure of the tree - which node has which key as a label**

### _Implementing Binary search tree_

- def Node {Node *parent, Node *left, Node \*right}
  - _Parent `ptr` is optional as, while traversing the `tree`, the `ptr` can be put on `stack` to **preserve the search order** and a way to trace back_

> **Note: Binary Search tree - Recursive structure**

- `Recursive Structure` - `if you make it smaller it is still of that type`

  - _Examples - Lists, Binary Search Tree_

- `Search time - BST` **proportional to** height of the tree `h`  (= depends on the BST =>  )
  - ***`O(h)`*** `(_think mR. anderson oO/<<!_)`

### Maximum and Minimum - BST

- _Left most element - Minimum_ ***`O(h)`***
- _Right most element - Maximum_ ***`O(h)`***

> NOTE: ***WORST CASE SCENARIOS - `BALANCED BST` Search Time = `O(log N)`***

### Where is Predecessor / Successor of a Node with a Key value `k` ?

- `Predecessor` - is the `maximum value` in the `left sub-tree`
- `Successor` - is the `minimum value` in the `right sub-tree` - `(_think mR. anderson oO/<<!_)`

### Where is the Predecessor : Leaf Node?

- if it ***doesn't*** have a `left child` then --- ? --- ***`predecessor is its first left ancestor`*** >> **`(_think mR. anderson oO/<<!_)`**
  - _the first RIGHT turning point before you reach the given node_
  - _Predecessor of the Minimum is `NULL`_
  - _`O(h)`_

### Tree Insertion

- _Insertion time - `O(h)`_
- _Do a Binary Search to find where the element should be and replace the termination `NULL` with the `new Node`_
- _For duplicate keys - we can have list as a Node_
- _BST - don't allow equality_

### Tree Deletion

- _Case 1 - where the Node is a leaf; just NULL out the Parent-child pointer_
- _Case 2 - where a Node has just one child; the doomed node can be just cut out_
- _Case 3 - where a Node has both the sub-trees; find the `Successor` by the definition above; re-label the Node with the  `Successor`; Delete the `Successor` Node_ `(_think mR. anderson oO/<<!_)` ***`O(h)`***
