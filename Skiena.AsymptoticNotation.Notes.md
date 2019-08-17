# Asymptotic Notation

## Ram model of computation

- Each simple  operation takes 1 step
- Loop are not simple operations
- Evey memory access takes 1 step

## We measure the run time of an algorithm by counting the number of steps

- Worst case complexity of an Algorithm is the function defined
by the maximum number of steps taken on any instance of size `n`

> This complexity defines a numerical function: time vs size
<hr/>

> **Exact analysis is hard !! yes it is**

- Best , Worst , Average case are difficult to deal with because `the precise` function details are very complicated
- It is `Easier` to talk about upper and lower bounds of the function
- Aysmptotic notation is the best way to practically deal with complexity functions

## After n0 for the values of n

- ***`g(n) = O(f(n))` means `C * f(n)` is an upper bound on `g(n)`***
- ***`g(n) = Omega(f(n))` means `C * f(n)` is a lower bound on `g(n)`***
- ***`g(n) = Theta(f(n))` means `C1 * f(n)` is an upper bound on `g(n)` and `C2 * f(n)` is a Lower bound on `g(n)`***

> Note: C, C1 and C2 are constants independent of `n`

<hr/>

## Big O examples

- 3n^2 - 100n + 6 = O(n^2) beacuse 3n^2 > 3n^2 - 100n + 6
- 3n^2 - 100n + 6 = O(n^3) beacuse 0.01 * n^3 > 3n^2 - 100n + 6
- 3n^2 - 100n + 6 = O(n) beacuse c*n < 3n^2 when n > c

***The equality sign means `in the set of functions`***
