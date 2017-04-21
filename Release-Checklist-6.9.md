* [ ] {Blockers}
  - [X] `gracket` and `gracket-text` are broken on Mac OS
  - [X] TR doc movement for refinements
  - [ ] workaround for Windows 10 Creators Update (OS bug)

* [ ] {John Clements <clements@brinckerhoff.org>}
  - [ ] Stepper Tests
  ```
  tests/stepper/run-manual-tests.rkt ;; run in DrRacket, ensure that expected failures occur.
  tests/stepper/manual-tests.txt ;; follow the instructions in this file
  ```

  - [ ] Updates:
    + [ ] Stepper Updates: update HISTORY

      (updates should show v6.9 as the most current version; email
      me to pick the changes when they're done, or tell me if there
      are no such changes.)

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [X] Match Tests:
  ```
  raco test -l tests/match/main
  ```
  
  - [ ] Typed Racket Tests:
  ```
  racket -l typed-racket-test -- --all
  ```
  
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show v6.9 as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

* [ ] {Ryan Culpepper <ryanc@ccs.neu.edu>}
  - [ ] Release tests for (one of the) linux releases:
    + [ ] Test that the `racket` and `racket-minimal` source releases
        compile fine.
    + [ ] Test that the binary installers for both work, try each one in
        both normal and unix-style installation modes.

* [ ] {Stevie Strickland <sstrickl@ccs.neu.edu>}
  - [ ] Unit Contract Tests
    ```
    raco test -l tests/units/test-unit-contracts
    ```

  - [ ] Contract Region Tests
    ```
    racket -l tests/racket/contract/define-contract
    racket -l tests/racket/contract/with-contract
    ```

  - [ ] Class Contract Tests
    ```
    racket -l tests/racket/contract/class
    ```

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

* [ ] {David Van Horn <dvanhorn@cs.umd.edu>, Sam Tobin-Hochstadt <samth@indiana.edu>}
  - [ ] EoPL Tests
    ```
    raco test eopl/tests
    ```

* [ ] {Neil Toronto <neil.toronto@gmail.com>}
  - [ ] Plot Tests
    ```
    raco test -c plot/tests
    ```
  - [ ] Images Tests
    ```
    raco test -c images/tests
    ```
  - [ ] Inspect icons
    ```
    raco docs icons # then look at them
    ```
  - [ ] Math tests
    ```
    raco test -c math/tests
    ```

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests
