# History Updates

* [ ] {John Clements <clements@brinckerhoff.org>}
  - [ ] Updates:
    + [ ] Stepper Updates: update HISTORY
      (updates should show v7.1 as the most current version; email
      me to pick the changes when they're done, or tell me if there
      are no such changes.)

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show v7.1 as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

* [ ] {Matthias Felleisen <matthias@ccs.neu.edu>}
  - [ ] Updates:
    + [ ] Teachpack Updates: update HISTORY
      (updates should show v7.1 as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

# Testing

* [ ] {Blockers}

* [ ] {Matthew Flatt <mflatt@cs.utah.edu>}
  - [ ] GRacket Tests (Also check that `gracket -z` and `gracket-text`
        still work in Windows and Mac OS X)
   ```
   racket -l tests/gracket/test
   gracket -z
   gracket-text
   ```
  - [ ] .plt-packing Tests
   ```
   racket -l tests/racket/test-pack
   ```
  - [ ] Games Tests
   ```
   plt-games
   ```
  - [ ] R6RS Tests
   ```
   racket -l tests/r6rs/run.sps   # 3 failures expected
   ```
  - [ ] PCPS test suite (in "pcps-test" repo)
   ```
   racket <file in pcps-test repo>
   ```
  - [ ] Create an executable from a BSL program
   ```
   # make big-bang program with literal image in DrRacket, 
   # then create executable
   ```
  - [ ] Run COM tests
   ```
   racket -l tests/racket/com
   ```
  - [ ] Embed-in-c test
   ```
   racket -l tests/racket/embed-in-c
   ```
  - [ ] Try compiling with `-funsigned-char`
   ```
   configure CPPFLAGS=-funsigned-char ; make
   ```
  - [ ] Try compiling with `TEST_ALTERNATE_TARGET_REGISTER`
   ```
   configure CPPFLAGS=-DTEST_ALTERNATE_TARGET_REGISTER=1 ; make
   ```
  - [ ] Run the unix installer tests (in "distro-build-test" package)
   ```
   racket -l distro-build/tests/unix-installer <version>
   ```

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

* [ ] {Stephen Chang <stchang@ccs.neu.edu>}
  - [ ] Lazy Racket Tests
    
    ```
    raco test -l lazy/tests/main.rkt
    ```
  - [ ] Lazy stepper tests

    ```
    raco test -l tests/stepper/automatic-tests.rkt
    ```

* [ ] {Mike Sperber <sperber@deinprogramm.de>}
  - [x] DMdA Tests
    [Test properties](https://gist.github.com/mikesperber/51851dc0540307721c24),
    [World teachpack](https://gist.github.com/mikesperber/84273cd5d097edf1cf0f)
  - [x] Stepper Tests
    [Check format of lists, records](https://gist.github.com/mikesperber/47b614c59930c2fbc7f1)
  - [x] Signature Tests
    [Test signatures](https://gist.github.com/mikesperber/1ba48601a944ecb38309)

* [ ] {David Van Horn <dvanhorn@cs.umd.edu>, Sam Tobin-Hochstadt <samth@indiana.edu>}
  - [ ] EoPL Tests
    ```
    raco test -c eopl/tests
    ```
