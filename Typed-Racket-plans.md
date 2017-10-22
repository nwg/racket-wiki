(last edited in 2014 - this needs updating)

# Typed Racket plans

This page focuses on internal issues in Typed Racket, although most of them also have user-visible results.

### Purity analysis

We should recognize that, eg,  `(< a b)` is pure and eliminate it if the result is unused.

### Better inference

Use something like colored local type inference or the system described in Jesse Tov's dissertation to propagate much more type information.  This should avoid the need to annotate lambdas in `map`, for example.

### Reduce the number of base types

We should have a general structure for representing type constructors that takes variance into account, and use it for things like `Vectorof`, `Parameterof`, `Boxof`, and so on.

### Support `#:names` declaration in `case->`

This will allow using names for parameter types in annotations in the body of functions with `case->` types.  [@stamourv](https://github.com/stamourv) is working on this.

### Support for generics (`racket/generic`)

May require research.

### Support multiple objects for expressions and aliasing of objects

We should be able to typecheck: `(let ((y x)) (if (number? y) (add1 x) 5))`