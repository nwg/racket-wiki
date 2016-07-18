* [ ] Decide whether to include macro-debugger commit 96ac3a

* [ ] {John Clements <clements@brinckerhoff.org>}
  - [ ] Stepper Tests
  ```
  tests/stepper/run-manual-tests.rkt ;; run in DrRacket, ensure that expected failures occur.
  tests/stepper/manual-tests.txt ;; follow the instructions in this file
  ```

  - [ ] Updates:
    + [ ] Stepper Updates: update HISTORY

      (updates should show `v$RKTNVER` as the most current version; email
      me to pick the changes when they're done, or tell me if there
      are no such changes.)

* [ ] {Ryan Culpepper <ryanc@ccs.neu.edu>}
  - [ ] Macro Debugger Tests
    ```
    racket -l tests/macro-debugger/all-tests.rkt -- --gui
    ```

  - [ ] Release tests for (one of the) linux releases:
    + [ ] Test that the `racket` and `racket-minimal` source releases
        compile fine.
    + [ ] Test that the binary installers for both work, try each one in
        both normal and unix-style installation modes.

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

