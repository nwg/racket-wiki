# **DRAFT** Migrating from Python to Racket 

**Contents**
* [Idioms](https://github.com/racket/racket/wiki/Python/#idioms)
* [Performance pitfalls ](https://github.com/racket/racket/wiki/Python/#performance-pitfalls)
* [References](https://github.com/racket/racket/wiki/Python/#references)

## Idioms

* A Python "List" is an extensible vector of pointers.

## Performance pitfalls 

* Python Lists aren’t Racket Lists
  * use either Growable Vectors or RaList
    * [Growable Vectors](https://docs.racket-lang.org/data/gvector.html)
    * [RaList: Purely Functional Random-Access Lists](https://docs.racket-lang.org/ralist/index.html)

* Python `append` isn't Racket `append`
  * Python's `append` adds a single element to the back of the List in amortized O(1) time.
  * Racket's append returns the concatenation of two or more Lists in O(n) time, making it more similar to
    Python's `extend` method (or the `+` operator for Lists).
  * To add single elements to a List, use the `cons` operator instead (adding elements to the front of a Racket
    List is a O(1) operation).
  * While building a List from the front may results in elements being in reverse order relative to the desired
    output, it is faster and more idiomatic to build call `reverse` after building the List than it is to try
    building the list from the back. This may seem counter-intuitive -- you're looping over the List twice! -- but
    it doesn't change the time complexity of O(n) or worse operations, and `reverse` is relatively fast.

### How to transliterate the loop/append example from python to Racket:


_optionally also show the more native Racket idiom_


## References

* [[Choosing a data-structure]]
* [Notes on data structures in Racket](https://alex-hhh.github.io/2019/02/racket-data-structures.html), with some performance considerations.