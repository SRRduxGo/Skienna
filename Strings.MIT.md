# Strings
[MIT](https://www.youtube.com/watch?v=NinWEPPrkDQ)
- Tries / Trays
- compressed trees
- suffix tree and array
- document retrieval
- linear-time construction

# Strings matching 
Text T -> String over Alphabet `Σ`
Pattern P -> String over Alphabet `Σ`

find some / all occurences of P in T as `substring`

Falvour -> Static Data Structure :: Preprocess T
Target is
- query: P
- in `Order(P)` time to do the query
- `Order(T)` space

Predecessor Problem to solve - 
 check where P fits in lexical order among
 set of strings T1, T2, T3, T4, T5... Tk (ordered lexically)
 ##solution is

- Binary Trees will not work here
- Build a `Trie`
- Trie is a rooted tree with child branches labeled with the `letters ∈ Σ` 
- To represent T` string as root-to-leaf paths
- Add a new letter `$` to the end of every string / at the end of a root-to-leaf path to indicate given string ends here - leaf represents a word
- A trie node can have as many paths emenating from it as the number of letters in alphabet `Σ` 

## Trie node repsentation
- array query time O(p) and space O(T*Σ)
- tree (BST)  time O(P*lg Σ) and space O(T) 
- hash table  time O(P) and space O(T) 
Problem with Hashing is it doesn't solve predecessor issue - who is the predecessor of whom?
-Weight Balanced Trees | {To be continued .... }





