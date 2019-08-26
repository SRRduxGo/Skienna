# [Heap-Sort / Priority Queues _(mains)_](https://youtu.be/yLvp-pB8mak?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b)

## oO/

> **Food For Thought - Two sets - whether they are Dis-Joint or total intersections? a set with n elements and a set with m elements. And n >> m**

<hr/>

### _Selection Sort - AFTERMATH :/_

> - ***`n log n` => `sort and find`*** the larger of the two and search the using the elements from the smaller set on the sorted larger set  ***( `n log n [sort time] +  m log n [search time]`)***
> - ***if we use a HashTable -  `O(m [hash table build time] . O(n) [search time]) ≈ O(nˆ2)`***
> - _optionally - `intersection = concatenate + sort + sweep` ..still it is `O(N log(N))`_

<hr/>

> **why deletion in a Binary tree takes `n log(n)` time - worst case? 0O/ think! and find**

- _Using `Array` or `unsorted linked-lists` as Data structure, Operation A will take `O(n)` time and B takes `O(1)` time, for `O(nˆ2)` `selection sort`_
- _But by using Balanced-BST OR **HEAPS**, both of these operations can be done within `log(n)` time and thus making `Selection Sort` an `O(n Log n)` algorithm_

> **What is the lesson of Selection Sort?**
> 

