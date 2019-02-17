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

* Python `append` isn't Racket `append`.
  * Python's `append` adds a single element to the back of the List in amortized O(1) time.
  * Racket's append returns the concatenation of two or more Lists in O(n) time. 
    * This makes it more similar to `extend` or `+` in Python.
  * Use the `cons` operator to add single elements to a Racket List (adding to the front of a Racket List is a O(1) operation).
  * Building a List from the front may result in elements being in reverse order, but it is faster and more
    idiomatic to build a List from the front and then correct the order by calling `reverse`. While this may seem counter-intuitive, `reverse` is relatively fast and won't change the time complexity of any O(n) or worse operations.

### How to transliterate the loop/append example from python to Racket:


_optionally also show the more native Racket idiom_


## References

* [[Choosing a data-structure]]
* [Notes on data structures in Racket](https://alex-hhh.github.io/2019/02/racket-data-structures.html), with some performance considerations.