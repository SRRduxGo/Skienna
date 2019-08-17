# Elementary Data Structures

[Skiena](https://www.youtube.com/watch?v=xoeBZNailFc&list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&index=4)

> ***Some Revision - `cˆ(log'c (x)) = x` simply put - Logarithm definition (intelligent one !)***
>
> ***`log'b (a) = log'c (a) / log'c (b) - Fun definition`***
>
> ***The BASE (of Log) is NOT Asymptotically important !***

## THE BEGINNING

### **_Mankind's ( The kinds in Tech specially ;) ) progress is measured by the number of things we can do without thinking_**

- **_Elementary data structures { Stacks, Queue, Lists, Heaps } are the `off-the-shelf` components we build our Algorithms from._**
- Two aspects to any Data structure:
  - The abstract operation it supports
  - The implementation of these operations

### **Data Abstraction**

- We should be able to _**Describe the behaviour** of our `Data Structures` in terms of **Abstract Operations**, is the reason why we can use `Data Structures` without thinking_
- There are different **implementations** of the same **Abstract Operation** enables us to optimize performance

### **Contiguous VS Linked Data Structures**

> **Think about these definitions in abstract terms, as to achieve the specs requires implementation**

- Data structures can be neatly classified as either **`Contiguous`** or **`Linked`** depending on whether they are based on `arrays` or `pointers`.

  - **`Contiguously-allocated`** structures are composed of **_`single slab of Memory`_** ex. _arrays, matricies, heaps and hash tables_
  - **`Linked`** data structures are composed of multiple distinct chunks of memory bound together by **_`Pointers`_** (ex. **_lists, trees, graph adjacency lists_**)

## **Arrays**

- An array is a structure of fixed-size data records
- Each element can be located by its Index or an Address

**Advantages of Contiguously-Allocated arrays**

- Constant-time access given the index _(HOW??)_
- Arrays consist purely of Data, so no space is wated with links or other formatting information

## **Dynamic Arrays**

- Advantage over simple arrays : Adjust size of the D-Array in the middle of the program execution
- With D-Array we start with an Array size of 1
  - Double its size from m to 2m each time we run out of space
  - For to reach size of `N` from 1 we need `log'2(N)` times doubling from size 1 (**why?**)
  - What is the Target Algo - How many times the copy operation has to happen from 1 to size N ?
  - Answer: `O( N.log(N) )` (**_why?_**)
  - Actually it is `O(2.N)`
    - Why - Waste in the procedure is recopying of the old content on each expansion
    - If half the elements move once, a Quarter of the elements move twice, and so on (**_why?_**)
    - Total no of movements `M` is given by
      - `M = ∑ ( i = 1 to Log N ) i.N/2ˆi = N ∑ ( i = 1 to Log N ) i / 2ˆi <= N ∑ ( i = 1 to Infinity ) i / 2ˆi`
      - `N ∑ ( i = 1 to Infinity ) i / 2ˆi = 2.N`
      - `M <= 2.N` hence `O(2.N)`
      - Clever.Tighter analysis would give us **Better Bound**

## **Pointers and Linked Structures**

- _**Pointers** represent the address of a location in the memory_

> Does it abstract out the memory model for developer's convinience ?
> Answer ??

- Concept of a **NULL** pointer
- **_Linked Lists and pointer manipulation_**

### Advantages of Linked Lists

>(_Over Static Arrays_)

- Overflow can never occur on LLists unless the memory is actually full

> This does not say Linked Lists require less memory than a corrsponding array (might take twice as much space)

- _Insertions and deletions are **Simpler** than for contiguous(Array) lists_
- _With large records, moving pointers is easier and faster than moving the items themselves_
- **Arrays** are more **_efficient_** but linked-lists provide more **_flexibility_**
- _Dynamic memory allocation provides us / affords us with the choice regarding how and where we use our limited storage resource_

## Stacks and Queues

- Sometimes, the order in which we retrieve data is independent of its content, _**being only a function of when the data arrived**_
- Stack = `last in first out`, Queue = `first-in, first-out`
- `Both can be used in tree traversals` find out how

## Dictionary / Dynamic set operations 

- Perhaps the most important class of Data-Structures | maintain set of items, indexed by keys
  - Search **_`(S,k)`_** - A query that,given a set **_`S`_** and a key value **_`k`_**, returns a pointer **_`x`_** to
  an element in **_`S`_** such that **_`key[x] = k`_**
  - Insert **_`(S,x)`_** - A modifying operation that augments the set **_`S`_** with the element **_`x`_**
  - Delete **_`(S,x)`_** - Given a pointer **_`x`_** to an element in the Set **_`S`_**, remove **_`x`_** from **_`S`_**
  - Min**_`(S)`_**, Max **_`(S)`_** - Returns the element of the totally ordered set **_`S`_** which has the smallest (largest) key
  - Next **_`(S,x)`_**, Previous **_`(S,x)`_** - Given an element **_`x`_** whose key is from the
  totally ordered set **_`S`_**, returns the next largest(smallest) element  in **_`S`_**, or `NIL` if x is the maximum(minimum) element
