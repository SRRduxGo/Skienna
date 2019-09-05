# [Merge Sort / Quick Sort](https://youtu.be/q7K9otnzlfE?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b)

## [PDF](https://www3.cs.stonybrook.edu/~algorith/video-lectures/2007/lecture8.pdf)

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

## Quick Sort

- In practice **Fastest `Internal` Sorting Algorithm**
- _uses `partitioning` as the main idea - around an element chosen as `PIVOT` | **not its `position` in the Array**_
- ***`Partitioning` places all the elements `less` than the `Pivot` in the `left` part of the `DataStructure` - Array***
- ***`Partitioning` places all the elements `greater` than the Pivot in the `right` part of the DataStructure - Array***
- _`Pivot` sits right in between the two (left/right) partitions_

> Example
>
>```js
>  ds = [8,10,11,3,4,5,7,1,11,12,34,56];
>  pvt = 10;
>  QuickSort_nonRecursive(ds,pvt) === [8,3,4,5,7,1,10,11,12,34,56] // is true;
>```

- _its an example of Randomized Algorithms_
- [**Best Case - time complexity - `O(N Log N)`**](https://youtu.be/q7K9otnzlfE?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=4087)
- _if the `Pivot` is not properly selected - `Worst Case` then ..should be `O(Nˆ2)` and YES IT IS the case (check why on a RE-VISIT (oO!) )_
  > HINT _In the Worst case the unexplored Array would reduce in size by `1` every time. Then how many comparisons each time?_

### [Partitioning the Elements](https://youtu.be/q7K9otnzlfE?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=3713)

- _We can partition an Array about the `Pivot` in one `Linear Scan` by maintaining three sections_
  - ***less than - `<` `Pivot`***
  - ***greater than - `>` `Pivot`***
  - ***`Unexplored`***
- _As we Scan from `Left` to `Right`_
  - _We move `left bound` to the right when `the element` is less than the `Pivot`_
  - _Otherwise we Swap `the element` with the `rightmost unexplored` element_
    - _Move the right bound one step closer to the left_
- At the end we swap the `Pivot` to its rightful position
  - _There are different ways to do that_
    - _Keep the `Pivot` element to the extreme right and then in the end swap it with the element holding the Right bound_
    >OR
    - _Move `Pivot` with every right swap : [shown here](https://www.youtube.com/watch?v=tIYMCYooo3c)_

### Why Partition _

- Since `partitioning` step consists of at most `N` position swaps - compare with the `PIVOT` and take the element to the `left` or the `right` partition - Since `SWAPS` are happening using the `Main Memory - RAM` as Buffer
  > OR **the Partitioning process described above** OR it really doesn't matter how you SWAP till the time it is `linear` and  no `inner-loops` - otherwise `nˆ2` Order would creep in

  - _Takes time linear in the number of the `keys`_
  - _The `Pivot` element ends up in the position it retains in the `Final` Sorted order_
  - _After `Partitioning`, no element flops to the other side of the `Pivot` in the `Final` sorted order_
  - _Now we can sort elements to the `right` and to the `left` of the `Pivot`, **`INDEPENDENTLY`**_

### Best Case for Quick Sort

- The best case for `Divide-And-Conquer` Algorithms come when we split the input - `N` as `evenly` as possible
- The `partition` step on each `subproblem` is `Linear` in its size
- ***Thus the total effort in `Partitioning`  the _`2ˆk`_ problems of size _`N/2ˆk`_, where `k = 1 to Log N` is `O(N)`***
- _Partitioning time complexity at each level is `O(N)`_
- _Number of levels - `Log N` - for perfect partitioning to get to single Element subproblem_
- _At `single-element` level - all the sub-problems are sorted_
  - _Because going before to the next sub-problem level `Partitioning` is already performed at the current level_
  - _This means as soon as we reach the `single-element` sub-problem level, the order of elements is sorted at the `last level`_
  - ***Remember NO BUFFER IS BEING USED - ALL THE CHANGES ARE PRESERVED IN THE SAME ARRAY***
- Thus total time complexity `Number of levels * time taken(complexity) at each level` = `log N * O(N)` = ***`O(N Log N)`***

### Worst Case for QuickSort

- 

