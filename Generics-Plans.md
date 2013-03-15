Planned features for Racket's generic functions library (`racket/generic`).

* Implement inheritance of partial method tables (see http://lists.racket-lang.org/users/archive/2013-March/056791.html)
* Polish the design of a `gen:buildable-sequence` interface (possible starting point: https://github.com/stamourv/buildable-sequences)
  * would be great if this came with a set of operations like `map/s`, `foldl/s`, `take/s`, etc. that just lets us not care about the type of sequence we're using.
* Speed up dispatch by using macro-introduced inline caches (tonyg has a starting point somewhere)
* Come up with a good multiple dispatch story that avoids mutation issues
* Design a `gen:set` interface (tricky bit: `set-union` of, e.g., a list-based set and a hash-based set)
* Integration with interfaces from Racket's object system
