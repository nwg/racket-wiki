# History Updates

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show v7.0 as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

# Testing

* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
  - [ ] Framework Tests:
   ```
   # from the top-level directory of the release bundle, run
   cd "$(dirname "$(./bin/racket -e '(display (collection-file-path "main.rkt" "framework" "tests"))')")"
   raco test .
   ```

  - [ ] PLaneT Tests: 
   ```
   # (the output of these tests is hard to read)
   raco test -l tests/planet/run-all
   ```

  - [ ] Release tests for the Windows release:
    + [ ] Test that the `racket-minimal` source release compiles fine.
    + [ ] Test that the binary installers for both work.

* [ ] {John Clements <clements@brinckerhoff.org>}
  - [ ] Stepper Tests
  ```
  tests/stepper/run-manual-tests.rkt ;; run in DrRacket, ensure that expected failures occur.
  tests/stepper/manual-tests.txt ;; follow the instructions in this file
  ```

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Match Tests:
  ```
  raco test -l tests/match/main
  ```
  
  - [ ] Typed Racket Tests:
  ```
  racket -l typed-racket-test -- --all
  ```


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

* [X] {Mike Sperber <sperber@deinprogramm.de>}
  - [X] DMdA Tests
    [Test properties](https://gist.github.com/mikesperber/51851dc0540307721c24),
    [World teachpack](https://gist.github.com/mikesperber/84273cd5d097edf1cf0f)
  - [X] Stepper Tests
    [Check format of lists, records](https://gist.github.com/mikesperber/47b614c59930c2fbc7f1)
  - [X] Signature Tests
    [Test signatures](https://gist.github.com/mikesperber/1ba48601a944ecb38309)

* [ ] {David Van Horn <dvanhorn@cs.umd.edu>, Sam Tobin-Hochstadt <samth@indiana.edu>}
  - [ ] EoPL Tests
    ```
    raco test -c eopl/tests
    ```

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests

