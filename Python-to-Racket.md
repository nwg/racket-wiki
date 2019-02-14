# **DRAFT** Migrating from Python to Racket 

**Contents**
* [Idioms](https://github.com/racket/racket/wiki/Python/#idioms)
* [Performance pitfalls ](https://github.com/racket/racket/wiki/Python/#performance-pitfalls)
* [References](https://github.com/racket/racket/wiki/Python/#references)

## Idioms 

* A Python "list" is an extensible vector of pointers


## Performance pitfalls 

* Python Lists aren’t Racket Lists 
  * use either Growable Vectors or RaList
    * [Growable Vectors](https://docs.racket-lang.org/data/gvector.html)
    * [RaList: Purely Functional Random-Access Lists](https://docs.racket-lang.org/ralist/main.html)

### How to transliterate the loop/append example from python to Racket:


_optionally also show the more native Racket idiom_


## References

* [[Choosing a data-structure]]
* [Notes on data structures in Racket](https://alex-hhh.github.io/2019/02/racket-data-structures.html), with some performance considerations. by [Alex Harsányi](https://alex-hhh.github.io/) 