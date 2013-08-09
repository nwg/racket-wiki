A wishlist of backwards incompatible things for a future Racket2.

**Note**: This is a wishlist. There's no guarantee any of these will be in a Racket2.

* Drop more guarantees about new object allocations: for example, allow `(append l '())` to return `l`,
  and the same for other list, string, bytes, vector functions (drop 0 items from the end of a list,
  `substring` and `regexp-replace` that don't change a string, etc).

* Remove `cond`'s default else-is-void clause and replace with a default else-is-error.

* Change `match` to recognize clauses based on bindings instead of symbols, and make
  it treat `else` like `cond`.

* Make every place where binding variables currently appear allow arbitrary match patterns (this requires some thought for handling what is currently things like `(define (f x) ..)`, so maybe we do this in a more limited way or change that way of defining functions to use a new keyword)

* Building on the match allowance, also allow functions to be defined case-by-case, for example maybe using a notation like this (roughly allowed in all internal definition contexts where `:=` is the keyword that triggers this kind of parsing):

        (length '()) := 0
        (length (cons x y)) := (+ 1 (len y))

And, even better, have this turn into `define/contract` or maybe `provide/contract` if something like this is written:

        length : (-> list? exact-nonnegative-integer?)
        (length '()) := 0
        (length (cons x y)) := (+ 1 (len y))

* Consider changing `cond` (and `match`) to use `#:else` instead of `else`.

* More prefabs for basic values, especially ones like srclocs where it is useful to make cross phase
  movements easy.

* Enable internal definitions everywhere.  (Note: this is tricky -- what's "everywhere"?
  Eg, can `define id` be followed by a definition(s) and then a value?  How about in the middle
  of an `if`?  Taken to an extreme, could definitions appear in an application form?)

* change syntax-case to allow internal definitions (possibly by getting rid of the 'guard' section)

* Enable the `define*` form (from `racket/package`) everywhere

* Use keywords in more places, such as unifying `member`, `memv`, `memf`, etc.

* Some syntax that avoids the verbosity in the `keyword-apply` etc kind of functions in the common
  case of passing keywords around.

* Some solution to the "no-value" value, which could be such a blessed value, or it could be a way
  to say that some function accepts all the keywords as some other function.  (Possibly related to
  the above, of course.)

* `struct` definition macro that allows
  - naming of the accessors/constructors/etc
  - ~~per-field `#:auto` values~~
  - ~~creating a constructor that takes all fields (when `#:auto` values should be something different)~~
  - ~~creating a constructor that makes `#:auto` fields optional keyword arguments~~
  - make `struct` have a function-like form that can specify auto values as optionals and/or keywords
  - maybe even allow several constructors with different argument "shapes"
  - more ideas from CL, like a `struct` keyword that actually use (tagged) lists for the values,
    similar to prefabs (and possibly redundant because of them)

* Have only either `struct` or `define-struct`. Not both.

* Disallow mutation of `struct` bindings.

* include pattern matching forms in more binding positions (e.g. `define`, `let`/`for` clauses)

* Generic programming by default: `map`, `fold`, and friends are generic and not specialized to lists.

* Change `integer?` to mean `exact-integer?`.

* Get rid of the `arity-at-least` struct, and replace it with just an `arity` that abstracts over the
  whole arity thing -- always normalizing and includes keyword arity information.  Also, make it possible
  to always use a procedure where an arity is expected.

* Reconsider printing and equality of mutable and immutable variants of data types (vectors,
  hash tables, strings, etc.). Also reconsider the coercion of mutable vectors to immutable
  vectors by `datum->syntax`.

* Add CLOS-like defmethod (with multidispatch and :before, :after, :around) on Racket classes.

* Add interactive breakpoint in DrRacket debug. One should have REPL at breakpoint

* Make strings immutable.

* Have `with-output-to-string` and friends take a body, not a thunk.

* Have `<`, `>` and others take 0 or more arguments (returning `#t` for the 0 and 1 argument cases). This would allow applying them to lists without fear, which would allow patterns like `(define (sorted? l) (apply < l))`

* Rename `racket/cmdline` to `racket/command-line`.

* Require that macro literals always be bound.
