Planned features for Racket's generic functions library (`racket/generic`).

* Implement inheritance of partial method tables (see http://lists.racket-lang.org/users/archive/2013-March/056791.html)
* Polish the design of a `gen:buildable-sequence` interface (possible starting point: https://github.com/stamourv/buildable-sequences)
  * would be great if this came with a set of operations like `map/s`, `foldl/s`, `take/s`, etc. that just lets us not care about the type of sequence we're using.
* Speed up dispatch by using macro-introduced inline caches (tonyg has a starting point somewhere)
* Come up with a good multiple dispatch story that avoids mutation issues
* Integration with interfaces from Racket's object system
* Add first-class documentation support to `scribble/manual` via `defgenerics`, likely similar to `defclass`/`definterface`

---

## Proposed extensions to the generics system

I (Alexis) have recently worked on implementing [a generic collections library](https://github.com/lexi-lambda/racket-alexis-collections). In doing so, I've found a few things I think need to be added to `racket/generic` to make everything operate smoothly.

### Implementation requirements

This is easy. Generic interfaces should be able to specify that implementations need to satisfy arbitrary contracts. This is most helpful when a certain interface is designed to be an extension of another. For example, to use an example from Haskell, given `gen:monad`, the following declaration should be possible:

```racket
(define-generics monad-plus
  #:implementation-contract monad?
  ...)
```

This doesn't need to be a part of the internal plumbing of generics, since it can just be applied as a contract to the individual methods.

### Interface instances for interfaces

This is a little more complicated, but this is probably what I'd find the most important to having a complete generics system. Take the following generic definitions:

```racket
(define-generics iterator
  (iterator-empty? iterator)
  (iterator-next iterator)
  (iterator-ref iterator))

(define-generics iterable
  ; iterable? -> iterator?
  (get-iterator iterable))
```

Now it needs to be possible to do something like this:

```racket
(struct cons-iterator (sequence)
  #:methods gen:iterator
  [(define (iterator-empty? v)
     (empty? (cons-iterator-sequence v)))
   (define (iterator-next v)
     (cons-iterator (rest (cons-iterator-sequence v))))
   (define (iterator-ref v)
     (first (cons-iterator-sequence v)))])

(define-generics cons-sequence
  (empty? cons-sequence)
  (first cons-sequence)
  (rest cons-sequence)
  #:methods gen:iterable
  [(define (get-iterator v) (cons-iterator v))])
```

I think having functionality like this is *essential* for providing an expressive generics system. The idea is that if you implement a certain interface, you can get an implementation of another interface "for free".