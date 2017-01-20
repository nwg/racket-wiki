* [ ] {Blockers}
  - [X] `drracket-vim-tool` regression.
        Status: Resolved
  - [X] Segfault in `multi-id`, `delay-pure`, `remember`, `phc-adt`, `phc-adt-test`, `phc-adt-lib`, `phc-toolkit`, `xlist`, `aful`, `typed-struct-props`, `extensible-parser-specifications`, and `type-expander`. Type errors in a subset of those.
        Status: Resolved
  - [ ] DrRacket documentation lookup bug reported by Matthias.

* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
  - [ ] Updates:
     + [ ] DrRacket Updates: update HISTORY
     + [ ] Redex Updates: update HISTORY (updates should show v6.8 as the most current version)
     + [ ] Ensure that previous version of DrRacket's preference files still starts up with new DrRacket
     + [ ] Update man pages in `racket/man/man1`: `drracket.1`

* [ ] {Ryan Culpepper <ryanc@ccs.neu.edu>}
  - [ ] Macro Debugger Tests
    ```
    racket -l tests/macro-debugger/all-tests.rkt -- --gui
    ```

  - [ ] syntax-parse Tests
    ```
    raco test -c tests/stxparse
    ```

  - [ ] RackUnit GUI Tests
    ```
    # not automated
    ```

  - [ ] Data Tests
    ```
    raco test -c tests/data
    ```

  - [ ] DB Tests
    ```
    # basic tests with sqlite3; other tests require local software & configuration
    racket -l tests/db/all-tests
    ```

  - [ ] Rackunit Tests
    ```
    # note: some tests are intended to fail
    racket -l tests/rackunit/run-tests
    ```

  - [ ] SRFI Tests
    ```
    racket -l tests/srfi/run-tests
    ```

  - [ ] Release tests for (one of the) linux releases:
    + [ ] Test that the `racket` and `racket-minimal` source releases
        compile fine.
    + [x] Test that the binary installers for both work, try each one in
        both normal and unix-style installation modes.

* [ ] {Stephen Chang <stchang@ccs.neu.edu>}
  - [ ] Lazy Racket Tests
    
    ```
    raco test -l lazy/tests/main.rkt
    ```
  - [ ] Lazy stepper tests

    ```
    raco test -l tests/stepper/automatic-tests.rkt
    ```

* [ ] {Stephen Bloch <sbloch1964@gmail.com>}
  - [ ] Picturing Programs Tests

* [ ] {Greg Cooper <greg@cs.brown.edu>}
  - [ ] FrTime Tests
    + [ ] Test that expressions with time-varying values (e.g., `seconds`,
        `(build-list (modulo seconds 10) identity)`) render and update as
        expected in the FrTime language level. Check that they continue
        updating even after a garbage collection.
    + [ ] Test that a sampling of graphical demos (e.g., `analog-clock.rkt`,
        `tetris.rkt`) work as expected, responding to relevant key and mouse
        events and interactions with control widgets.

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests
