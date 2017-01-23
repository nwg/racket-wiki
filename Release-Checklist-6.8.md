* [X] {Blockers}
  - [X] optimizer bug related to zero-values binding and detected errors
  - [X] `drracket-vim-tool` regression.
        Status: Resolved
  - [X] Segfault in `multi-id`, `delay-pure`, `remember`, `phc-adt`, `phc-adt-test`, `phc-adt-lib`, `phc-toolkit`, `xlist`, `aful`, `typed-struct-props`, `extensible-parser-specifications`, and `type-expander`. Type errors in a subset of those.
        Status: Resolved
  - [X] DrRacket documentation lookup bug reported by Matthias. (Not fixed, but not blocking the release.)

* [ ] {Greg Cooper <greg@cs.brown.edu>}
  - [ ] FrTime Tests
    + [ ] Test that expressions with time-varying values (e.g., `seconds`,
        `(build-list (modulo seconds 10) identity)`) render and update as
        expected in the FrTime language level. Check that they continue
        updating even after a garbage collection.
    + [ ] Test that a sampling of graphical demos (e.g., `analog-clock.rkt`,
        `tetris.rkt`) work as expected, responding to relevant key and mouse
        events and interactions with control widgets.
