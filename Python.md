# **DRAFT** Migrating from Python to Racket 

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

[[Choosing a data-structure]]

[draft notes on data structures in Racket(gist)](https://gist.github.com/alex-hhh/3cc5690a7f9c74543dab6c11344e6202), with some performance considerations. by [Alex Harsányi](https://alex-hhh.github.io/) 