# Dictionary

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

- def Node {Node *parent, Node *left, Node *right}
  - _Parent ptr is optional as while traversing a tree, the ptr can be put on stack to preserve the search order and a way to trace back_
- __
