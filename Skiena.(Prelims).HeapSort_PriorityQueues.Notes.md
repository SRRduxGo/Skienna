# [Heap-Sort / Priority Queues _(prelim)_](https://youtu.be/ute-pmMkyuk?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b)

> ***think about `log Nˆ2` and `logˆ2 N` or `(log N)ˆ2` and `log log N or log (log N)`***

<hr/>

> _Problem of the Day: Take as input a sequence of 2n real numbers. Design an `O(n log n)` algorithm that partitions the number into `n` pairs, with the property that the partition minimizes the maximum sum of the pair?_

<hr/>

> **[Proof by contradiction](https://youtu.be/ute-pmMkyuk?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=1253) and correctness**

## How sorting is used to solve problems - (the problem above >oO< !)

### Importance of SORTING

- Computers spend more time sorting than doing anything else
- Sorting is the best studied problem in computer science with a variety of different algorithms known
- Interesting ideas can be understood with the context of `Sorting`

### Efficiency of Sorting

- Once the set of items is sorted, many other problem related to that set becomes easier to solve
- using **`O(n log n)`** sorting algorithms lead naturally to sub-quadratic problems

### Application of Sorting

- `Binary search` - lets you test whether an item is in a Dictionary in **`O(log n)`** time
  - _`Binary search` can be used to find a `SQR-Root` of a number - Do a `Binary Search` between `0 to N`_
  > Median between to numbers a and b, why is it (a+b)/2 ?
  
- `Closest Pair` - Given n numbers, find the pair which are closest to each other?
  - _Once the numbers are **sorted** the `Closest Pair` will be next to each other_
  - _`O(n)` linear scan will complete the job after sorting_

- `Element Uniqueness` - Given a set of N elements, are they all unique or are there any duplicates?
  - _Sort them and do a linear sweep to check all the adjacent pairs_

- `Mode` - Given a set of `n` items, which element occurs the largest number of times? Compute the frequency distribution
  - _Sort them and do a linear scan to measure the length of all adjacent runs_
  - _**The number of instances of `k` in a sorted array can be found in `O(log n)` time by using binary search to look for the positions of both `k - e` and `k + e`**_
  > _`clever oO!`_

- `Median and Selection` - `what is the kth largest item in the set?`
  - _Once the keys are placed in sorted order in an array, the `k`th largest can be found in constant time by looking at the `k`th position of the array_
  - _Same goes for finding the `median` = `n/2`_

- `Convex Hulls` - Given `n` points in two dimensions, find the smallest area polygon which contains them all?
  - _The **convex hull** is like a rubber band stretched over the points_
  - _Refer `Skiena` book_
    - _Once you have the points sorted by `x-coordinate`, they can be inserted from `left to right` into the `HULL`_
    - _the rightmost point is always on the boundary_

### [Pragmatics of Sorting](https://youtu.be/ute-pmMkyuk?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=3826)

#### Comparison Functions

- Explicitly controlling the order of the `keys` is the job of the ***`comparison functions`*** we apply to each pair of elements
- This is the way to resolve the question of `Increasing or Decreasing` function

#### Equal Elements

- Elements with equal `keys` gets bunched together in any total order
- **Some times relative order among these keys matter**
  - _**Sorting Algorithms that always leave equal items in the same relative order as in the original permutation are called stable**_
  - **Stability** can be achieved by adding the initial position as a `secondary key`

#### Selection Sort

- `Selection Sort` scans through an entire Array, repeatedly finding the smallest remaining element

```js

for i = 1 to n
    A: Find the smallest of the first (n - i + 1) items
    B: Pull it out of the Array and `SWAP` it with the first
    // Search Size of the Array keeps on decreasing
```

- `Selection Sort` takes ***`O(n(T(A) + T(B)))`*** time = ***`O(n(n + 1) ≈ O(nˆ2)`***
- ***FIND A BETTER DATA STRUCTURE TO DO BOTH JOBS, `A` AND `B`, IN LESS TIME THAN `O(nˆ2)` ??***

> if we use a Balanced-BST for **SelectionSort** the time taken would be `N Log N`, which can also be done using a DataStructure called **HEAP**
