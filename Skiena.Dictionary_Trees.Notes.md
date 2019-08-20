# Dictionary / Trees

## Binary Search Trees as Dictionaries

### Dictionary Operations

- _All six of Dictionary operations (BST Implementation) take **`O(h)`** ⇒ `h` is the height of the tree_
- _BEST height of a tree we could hope for is `Log N` - `N` number of nodes in a tree - if the tree is `perfectly Balanced`_
- ***`∑ (i = 0 to Log N ) 2ˆi ≈ N`*** _`(think mR. anderson oO/<<)`_
- _But if we get un-lucky with our order of insertion and deletion, we could get linear height_

> Note: If we construct a tree out of a sorted List(NOT RANDOM but follow the order of the GIVEN LIST) then we get a BS-Tree with all Six operations time complexity ≈ `O(N)`; this is because it will just be a BST with BIG BIG right [arm](https://youtu.be/Juv4AsnnqMA?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=298) ;)

### Tree Insertion Analysis

- BST constructed with Random Insertion orders (from example from a sorted List or otherwise) **On average** have **`O(log N)`** height
  - _Root, ideally, should have the Median value of the given values/keys_
- **Worst case is LINEAR (if, Randomly, we end up getting the Nodes to be inserted, in a sorted order)**

### Perfectly Balanced BS-Trees

- Takes a lot of work to maintain them - after an insertion it might take `O(N)` time (WORST TIME) to re-balance it
- Tree height is `O(Log N)`, not exactly `Log N`, because that doesn't give you enough freedom to make fast updates
  - _Tree with height `2 Log N` the `Nˆ2` Nodes_
- All Dictionary operations will take `O(log N)` time
  - _Examples of balanced trees - Red-Black trees, AVL trees, 2-3 Trees, Splay Trees, B-Trees_
- _Try to solve problem of the [Day](https://www.youtube.com/watch?v=Juv4AsnnqMA&list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&index=6)_ (oO/<< `O(n.Log(n))` !! )
  - _[Another Problem](https://youtu.be/Juv4AsnnqMA?list=PLOtl7M3yp-DV69F32zdK7YJcNXpTunF2b&t=1463)_
- **Related to how to think about Balanced Binary Search Trees while designing Algorithms**

> Note: It takes linear time to do in-order traversal in a BST

### Hash Tables - Implementation of Dictionaries

> ***`The test of a first-rate intelligence is the ability to hold two opposed ideas in mind at the same time and still retain the ability to function`***

> Opposing Ideas being - Worst Case Analysis VS Useful Tricks (Hash Tables don`t give guarantees in terms of Big O)

- One example of A `hash function` is a `Mathematical function` which map keys to integers
  - _An array is a good example - `O(1)` time complexity if you know the Index of the element_
- .. It's a Job of the Hash function to 
  - .Map keys to Integers.
  - .Is cheap to evaluate.
  - .Tends to use all positions from 0..M with uniform frequency
  - .one such hash function `hsh = ∑(i = 0 to keylength) 128ˆi * char(key[i])`. (not a cheap function though)
    - .why `128` in above equation? because there are `128` ASCII characters. `BASE'128 Number`
  - .optimizing the hash function `hsh = ∑(i = 0 to keylength) 128ˆi * char(key[i])`.
    - .The large number must be reduced to an integer whose size is between 1 and SIZE of the HASH TABLE.
    - .one way is `hsh mod M` which gives a Remainder (number between 0 and M-1).
      - _Works on the same principle as a roulette wheel_

#### Collisions

- is the set of the `keys` mapped to the same bucket
- If the `keys` are uniformly distributed then each bucket should contain very few `keys` or Collisions
- `These BUCKETS` are short lists then and can be easily searched
- _A GOOD HASH FUNCTION SCATTER THINGS AROUND RANDOMLY_
- _ _


