# Program Analysis

> O(f(n)).O(g(n)) = O(f(n).g(n))

<hr/>

> Omega(f(n)).O(g(n)) = Omega(f(n).g(n))

<hr/>

> Theta(f(n)).O(g(n)) = Theta(f(n).g(n))

## Reasoning and Efficiency

- Grossly reasoning about the running time of an algorithm is easy
  given precise enough written description of the algorithm
- when you `really` understand an algorithm, this analysis can become mental
- **Recognize** that there is always implicitly a written algorithm / program we are reaoning about
- Big O , Theta , Omega are the ways to talk about functions in General not limited to Algorithms
- **_`Learn about Asymptotic Dominance`_**

> Note: It is usually number of operation steps `n` per unit of Instance which boils down to `n.f(N)` steps ( **How many times** do we have to repeat this `n` steps block (per unit instance) for the Given Instance of size `N`. This number **_HOW MANY TIMES_** is important and usually it is a function of total Instance size - `N` ) if the instance size is `N`. We have to study the effects of _`if N keeps varying`_ to time / space taken by the algorithm

## Implication of dominance

- Exponential algorithms get hopeless fast
- Quadratic algorithms get hopeless at or before `1,000,000` (6 zeroes)
- O(n.log(n)) is possible to about one billion `1, 000, 000, 000` (9 zeroes)
- O(log(n)) never sweats

## Testing dominance

- f(n) dominates g(n) if lim (n -> Infinity) g(n)/f(n) = 0,
  which is the same as saying g(n) = o(f(n))
- Little `o` means `grows strictly slower than`

## Properties of Dominance

- n^a dominates n^b if a > b since
  - _lim (n -> Infinity) n^b / n^a = n^(b-a) -> 0_
- n^a + o(n^a) doesn't dominate n^a since
  - _lim (n -> Infinity) n^a / (n^a + o(n^a)) -> 1_

## Dominance Ranking

- n! >> 2^n >> n^3 >> n^2 >> n log(n) >> n >> log(n) >> 1

## Logarithms

- _A logarithm is simply an `inverse exponential function`_
- _Saying b^x = y is equivalent to saying that x = log`b (y)_
- _Logarithm reflects(approx.) how many times we can double something until we get to the target value_

> ***OR***

- _How many times we can halve something until we get to 1_

> NOTE : _We focus on the **`x`** of `x = Log N` but not the base ( ie 2, 8 etc..) of the Log function._

<hr/>

> ## Think..! - what this **actually** means and **why this is true** \*\*_`log'a(x.y) = log'a(x) + log'a(y)`_
