A wishlist of backwards incompatible things for a future Racket2.

* Drop more guarantees about new object allocations: for example, allow `(append l '())` to return `l`,
  and the same for other list, string, bytes, vector functions (drop 0 items from the end of a list,
  `substring` and `regexp-replace` that don't change a string, etc).

* Remove `cond`'s default else-is-void clause and replace with a default else-is-error.

* More prefabs for basic values, especially ones like srclocs where it is useful to make cross phase
  movements easy.

* Enable internal definitions everywhere.  (Note: this is tricky -- what's "everywhere"?
  Eg, can `define id` be followed by a definition(s) and then a value?  How about in the middle
  of an `if`?  Taken to an extreme, could definitions appear in an application form?)

* Enable the `define*` form (from `racket/package`) everywhere

* Use keywords in more places, such as unifying `member`, `memv`, `memf`, etc.

* `struct` definition macro that allows
  - naming of the accessors/constructors/etc
  - ~~per-field `#:auto` values~~
  - ~~creating a constructor that takes all fields (when `#:auto` values should be something different)~~
  - ~~creating a constructor that makes `#:auto` fields optional keyword arguments~~
  - make `struct` have a function-like form that can specify auto values as optionals and/or keywords
  - maybe even allow several constructors with different argument "shapes"
  - more ideas from CL, like a `struct` keyword that actually use (tagged) lists for the values,
    similar to prefabs (and possibly redundant because of them)

* include pattern matching forms in more binding positions (e.g. `define`, `let`/`for` clauses)

* Generic programming by default: `map`, `fold`, and friends are generic and not specialized to lists.

* Change `integer?` to mean `exact-integer?`.

* Get rid of the `arity-at-least` struct, and replace it with just an `arity` that abstracts over the
  whole arity thing -- always normalizing and includes keyword arity information.
