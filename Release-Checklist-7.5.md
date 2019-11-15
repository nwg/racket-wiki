
# History Updates

* [ ] {Matthew Flatt <mflatt@cs.utah.edu>}
  - [ ] Updates:
    + [ ] Racket Updates: update HISTORY (updates should show v7.5 as the most current version)
    + [ ] Update man pages in `racket/man/man1`: `racket.1`, `gracket.1`, `raco.1`

* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
   - [ ] Updates:
     + [ ] DrRacket Updates: update HISTORY

* [ ] {John Clements <clements@brinckerhoff.org>}
  - [ ] Updates:
    + [ ] Stepper Updates: update HISTORY
      (updates should show v7.5 as the most current version; include
      the text "merge" in the commit message, or tell me if there
      are no such changes.)

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show v7.5 as the most current version; include
      the text "merge" in the commit message, or tell me if there 
      are no such changes.)

# Testing

* [ ] {Blockers}
  - `in-dict` with a-lists: https://github.com/greghendershott/aws/issues/64
  - compilation failure in `psd` package

* [ ] {John Clements <clements@racket-lang.org>}
  - [ ] FrTime Tests
    + [ ] Test that expressions with time-varying values (e.g., `seconds`,
        `(build-list (modulo seconds 10) identity)`) render and update as
        expected in the FrTime language level. Check that they continue
        updating even after a garbage collection.
    + [ ] Test that a sampling of graphical demos (e.g., `analog-clock.rkt`,
        `tetris.rkt`) work as expected, responding to relevant key and mouse
        events and interactions with control widgets.

* [ ] {Stephen Chang <stchang@ccs.neu.edu>}
  - [ ] Lazy Racket Tests
    
    ```
    raco test -l lazy/tests/main.rkt
    ```
  - [ ] Lazy stepper tests

    ```
    raco test -l tests/stepper/automatic-tests.rkt
    ```
* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests

