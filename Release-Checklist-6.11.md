* [ ] {Blockers}
  - https://github.com/racket/racket/commit/22e8af32f318dd1361ee58c34baae9f3e2fdb93f

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

* [ ] {Matthias Felleisen <matthias@ccs.neu.edu>}
  - [ ] Teachpacks Tests: check that new teachpacks are addable
      ```
      1. create foo.rkt: #lang racket (define x 0) (provide x)
      2. create bar.rkt: #lang htdp/bsl (require "foo.rkt") x; RUN and check for 0 to pop out
      3. delete require line, use teach pack menu to add foo.rkt; RUN and check for 0 to pop out
      4. delete foo.rkt and bar.rkt
      ```

  - [ ] Teachpack Docs: check teachpack docs in the bundles
      ```
      type "big-bang" into Definitions area, highlight, use F1; check for manuals 
      ```

  - [ ] Try teaching-languages testing framework (check-expect)
      ```
      run tests in plt: extra-pkgs/htdp/htdp-test/tests/test-engine/
      ```

  - [ ] Updates:
    + [ ] Teachpack Updates: update HISTORY
      (updates should show `v$RKTNVER` as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

* [ ] {Vincent St-Amour <stamourv@racket-lang.org>}
  - [ ] Release tests for (one of the) linux releases and the Mac OS release:
    + [ ] Test that the `racket` and `racket-minimal` source releases
        compile fine.
    + [ ] Test that the binary installers for both work, try each one in
        both normal and unix-style installation modes.
  - [ ] FrTime Tests
    + [ ] Test that expressions with time-varying values (e.g., `seconds`,
        `(build-list (modulo seconds 10) identity)`) render and update as
        expected in the FrTime language level. Check that they continue
        updating even after a garbage collection.
    + [ ] Test that a sampling of graphical demos (e.g., `analog-clock.rkt`,
        `tetris.rkt`) work as expected, responding to relevant key and mouse
        events and interactions with control widgets.
  - [ ] Inspect icons
    ```
    raco docs icons # then look at them
    ```



* [ ] {Stephen Chang <stchang@ccs.neu.edu>}
  - [ ] Lazy stepper tests

    ```
    raco test -l tests/stepper/automatic-tests.rkt
    ```
