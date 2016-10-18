* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
   
   - [ ] Updates:
     + [ ] DrRacket Updates: update HISTORY
     + [ ] Redex Updates: update HISTORY (updates should show v`$RKTNVER` as the most current version)
     + [ ] Ensure that previous version of DrRacket's preference files still starts up with new DrRacket
     + [ ] Update man pages in `racket/man/man1`: `drracket.1`

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

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>, Vincent St-Amour <stamourv@ccs.neu.edu>}
  - [ ] Match Tests:
  ```
  raco test -l tests/match/main
  ```
  
  - [ ] Typed Racket Tests:
  ```
  racket -l typed-racket-test -- --all
  ```
  
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show v$RKTNVER as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

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

* [ ] {Mike Sperber <sperber@deinprogramm.de>}
  - [ ] DMdA Tests
    [Test properties](https://gist.github.com/mikesperber/51851dc0540307721c24),
    [World teachpack](https://gist.github.com/mikesperber/84273cd5d097edf1cf0f)
  - [ ] Stepper Tests
    [Check format of lists, records](https://gist.github.com/mikesperber/47b614c59930c2fbc7f1)
  - [ ] Signature Tests
    [Test signatures](https://gist.github.com/mikesperber/1ba48601a944ecb38309)

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
