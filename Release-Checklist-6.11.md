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

* [x] {Matthias Felleisen <matthias@ccs.neu.edu>}
  - [x] Teachpacks Tests: check that new teachpacks are addable
      ```
      1. create foo.rkt: #lang racket (define x 0) (provide x)
      2. create bar.rkt: #lang htdp/bsl (require "foo.rkt") x; RUN and check for 0 to pop out
      3. delete require line, use teach pack menu to add foo.rkt; RUN and check for 0 to pop out
      4. delete foo.rkt and bar.rkt
      ```

  - [x] Teachpack Docs: check teachpack docs in the bundles
      ```
      type "big-bang" into Definitions area, highlight, use F1; check for manuals 
      ```

  - [x] Try teaching-languages testing framework (check-expect)
      ```
      run tests in plt: extra-pkgs/htdp/htdp-test/tests/test-engine/
      ```

  - [x] Updates:
    + [x] Teachpack Updates: update HISTORY
      (updates should show `v$RKTNVER` as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

* [ ] {Stephen Chang <stchang@ccs.neu.edu>}
  - [ ] Lazy stepper tests

    ```
    raco test -l tests/stepper/automatic-tests.rkt
    ```
