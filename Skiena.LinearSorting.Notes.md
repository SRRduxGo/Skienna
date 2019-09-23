# [Linear Sorting](https://youtu.be/TvqIGu9Iupw?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b)

> Problem of the day
>
> The Nuts and Bolts problem is defined as follows:
>
> - Collection of `N bolts` of different `widths` and `N` corresponding `nuts`
> - _You can test the Given `Nut` and `Bolt` together for `Too Large`, `Too Small` or `An exact match`_
> - _Match each `Bolt` to each `Nut`_
> - _Each `Nut fits exactly one Bolt`_
>
> ## Solution
>
> A naive algorithm can be `O(nˆ2)`, comparing each Nut with each Bolt
>
> To find the smallest Bolt and the Nut can be done in `2n - 2` comparisons
>  
> - Pick a Nut and compare with the Bolts to find a match or a smaller bolt. Discard the bolts which were `large` in size
> - compare the smaller bolt found with the nuts to find a match or a smaller nut. Discard the nuts which are `large` in size compared to the bolt
> - _Worst case the smallest of the Nuts and the Bolts must be at the end of the two collections  - minimum `2n` comparisons_
>
> TO Match Nuts and Bolts in `expected` `O(n Log n)` time
>
> - _use a Bolt to partition the Nuts and find the matching Nut as well_
> - _use the found nut to partition the Bolts_
> - _use the above two steps recursively to partition the `partitions` from the previous steps using a Bolt for Nuts and a Nut for the Bolts_
> - _Eventually both the partition Trees will have leaves in sorted order_
> - _This is Average case `Quick Sort` - `O(N Log N)`_
> - _Merge Sort will fail here. But why?? oO!_
> - _Something to read about #`Randomized Quicksort`#_
>
> Randomized Algorithms

<hr/>

> Side Note: Importance of Randomization
>
> Since time bound doesn't depend on your input distribution, this means that if we are `extremely` unlucky, we will certainly get good performance.
> Randomization is a general tool to improve Algorithms with `BAD Worst Case` but good `Average-case` complexity. The worst case is still there, but we almost certainly won't see it

## Can we sort `o(N Log N)`?

- ***Any comparison based sorting  program can be thought of as `defining` a decision trees of possible executions***
- ***Running the same program `twice` on the `same permutation` causes it to do exactly the `same thing`***
  - **Same path in the Decision tree would be traversed**
- ***BUT running it on `different permutations` of the `same Data` causes a `different sequence` of comparisons to be made on each***
  - **A different path would be traversed to reach a different `leaf`, difference in terms of `input permutation` but `the same solution`**

### **Claim: The `height` of this `decision tree` is the `worst-case` complexity of Sorting or Worst case input permutation**

- ***Now same set of elements can be in `any permutation`, if there are `n` elements then there can be `n!` permutations of the same elements***

> A different way to look at a comparison Algorithms

#### Interpret Any Sorting Algorithm as a Tree of Executions

- _where `leaf - s` correspond to the distinct inputs to the sorting Algorithm_
- _the `Execution - path` of the Tree determines the response to the input_
- _Height of the tree is the `worst-case-input` to that Tree_

> If we look at the given Input abstractly - the input elements respective values do not matter - but what order they are in / permutation matters. If we stuff comparison-truth between the elements in a given permutation:
> Example - `[x,y,z,q,k,l,m]` => `[x>y<z=q<k<l>m]`
> And also maintain a separate individual comparison-truth table of each element with all other elements of the Input then any `Input` with different set of `elements` but with `same comparison-truth order and table order`, will  always result in the same `Execution-path` to be traversed

- _if input size is `N` then height of the `Execution Tree`, assuming it is balanced, is going to be `Log N!`_

#### Lower Bound Analysis

- ***Since any two different permutations  of `N` elements require  a different sequence of `steps to sort` or a `Execution path`, there must be `at least` `N!` different paths from the root to leaves in the decision tree***
- ***Thus there must be `at least` `N!` different leaves in this binary tree***
- ***Since binary tree of height `h` has at most `2`<sup>`h`</sup> leaves***
  - **`N! ≤` `2`<sup>`h`</sup> OR**
  - **`h ≥ Log N!`**
- ***By inspection `N! > (N/2)`<sup>`N/2`</sup>***
  - **Since the last `N/2` terms of the product are each greater than `N/2`. Thus**
- ***`Log N!  > Log( (N/2)`<sup>`N/2`</sup>`) = N/2 Log N/2 ⇛ Θ (N Log N)`***
  - ***`Log N!  > Θ(N Log N)`***
  - **It means any `Comparison` based `Sort` Algorithm cannot be faster than `N Log N`**

## Non Comparison Based Algorithms

### Bucket Sort

#### Suppose we are sorting `n` numbers from `1 to m`, where we know the numbers are approximately uniformly distributed

- _We can set  up `n` `buckets`, because if the numbers are `uniformly distributed` then it should be `1`member per `bucket`_
  - _To `sort` a `bucket` with `1` member will take `O(1)` time_
- _Each bucket will be responsible for `m/n` numbers from `1 to m`_
  - _the first bucket will have `1 to m/n` numbers_
  - _the Second bucket will have `(m/n + 1) to 2.m/n` numbers_
  - _the last bucket will have `(m - m/n) to m` numbers_
- _To decide which bucket a given number `x` will fall in, compute `floor(x * n/m)` - how many `m/n`s have to be added together to get the given number `x`_
- _if we use an array of buckets, each item gets mapped to the right bucket in `O(1)` time_

#### Bucket Sort Analysis

- _With uniform distributed keys, the expected number of items per bucket is `1`_
- **Hence sorting each bucket takes `O(1)` time**
- **The total effort of bucketing `n * O(1) = O(n)`, sorting buckets `O(1)` and concatenating `O(n-1)` the sorted buckets together is `O(n) + O(1) + O(n - 1) = O(n)`**
