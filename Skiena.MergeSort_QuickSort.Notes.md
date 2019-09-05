# [Merge Sort / Quick Sort](https://youtu.be/q7K9otnzlfE?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b)

## Problem of the day

> **Given an array based heap of `N` elements and a real number `X`, efficiently determine whether the `kth` SMALLEST element in the `HEAP` is `greater than or equal` to `X`. Your Algorithm should be `O(k)` in the worst case, independent of the size of the HEAP ?**

<hr/>

> **Solution**:  _Heap is very good at extracting the MIN number - to read `k` min elements will take `O(k log n)` time complexity, while keeping the `HEAP` `happy`._
>
> - _`ONE POSSIBLE SOLUTION` - Keep moving to the next min-element, using `A pointer`, till the time you have moved `k` times, worst case would be the height of the tree - One can say `O(log N)` < `O(N)`_
> - _`ONLY SCAN TILL K'th LEVEL` - `k`th SMALLEST element cannot be below the `k`th level - `O(2ˆk)` OR `O(2ˆmin(k,log N))` - JUST SCAN all the elements till `k`th level_
> - _`COMBINE THE TWO  - STATED ABOVE` - Keep comparing with `X` and keep hoping to the next min node till you reach the `k`th level or `k`th Node - Since it's a Binary Tree, worst case would be scanning twice as many nodes `2k` since, before we move the pointer forward we would have to, worst case, compare both the `child` nodes to find out which is less than `X` and then move the `pointer` to that `child` node - Running time `O(2k) ≈ O(k)`_
> - __

## Merge Sort

- Recursive Algorithms are based on reducing large problems into small ones
- Recursive Approach to Sorting
  - _partitioning the elements into two groups_
  - _Sorting each of the two smaller groups recursively_
  - _`interleaving` the two sorted groups to `totally order` the elements_
    - _Partitioning into two groups will lead to a tree like structure with height approx `log N` | `N` total number of elements_
    - _At each level of the tree `interleaving` adjacent two sorted groups will take `O(N)` time_
    - _Since it has `O(log N)` height/level **⤇** Algorithm time complexity `O(N log N)`_
  - _The efficiency of `Merge-Sort` depends upon_
    - _efficient combination of two sorted halves into a single sorted list_
  - _It is **INCONVENIENT** to implement `Merge-Sort` wit **Arrays**, since it requires extra space to merge the arrays at each level_
  - _Writing the Merged List to a `BUFFER` and recopying it will require extra space but not extra time_

  > _Analyse the Algorithm using an Array and Buffer ONCE oO)!_
  
  <hr/>
  
  > SIDE NOTE:
  >
  > ## DIVIDE AND CONQUER
  >
  > - **This technique is used in a number of Algorithms:**
  >   - _MergeSort_
  >   - _Binary Search_
  >   - _The Fast Fourier Transform_
  >   - _Strassen's Matrix Multiplication Algorithm_
  > - We divide the problem into two smaller sub problems
  > - Solve each recursively
  > - Then meld the two partial solutions into ONe Solution
  > - When merging takes less time than solving the two sub-problems - we get an efficient  algorithm

<hr/>

  > Non-TRIVIA: which `O(N Log N)` doesn't matter much until `N` is so big that DATA doesn't fit in the memory
  > DISKS are much slower than the memory, and for the case above, benefit from algorithms that read and write data in long streams - NOT RANDOM ACCESS
  > `MergeSort` is one of the efficient external sorting algorithms { which use disk space other than RAM}

## 