This page shows the state of testing for the 6.5 release. When you are done with items, either edit this page to **delete the items** (and your entire entry, when all of your items are done) or email Ryan and he will update this page.

List release-stopping issues here:
  * none yet

----

* [ ] {Matthew Flatt <mflatt@cs.utah.edu>}
  - [ ] GRacket Tests (Also check that `gracket -z` and `gracket-text`
        still work in Windows and Mac OS X)
   ```
   racket -l tests/gracket/test
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

  - [ ] Updates:
    + [ ] Racket Updates: update HISTORY (updates should show v`$RKTNVER` as the most current version)
    + [ ] Update man pages in `racket/man/man1`: `racket.1`, `gracket.1`, `raco.1`
    + [ ] Email me to pick the changes when they're done, or tell me if
          there are no such changes.

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
    + [ ] Test that the `racket` and `racket-textual` source releases
        compile fine (note that they're still called `plt` and `mz` at
        this stage).
    + [ ] Test that the binary installers for both work, try each one in
        both normal and unix-style installation modes. (just ubuntu)
      [Note: get the release candidates from the URL in this email. Use
       the 'static table' link to see a list of all tar files available]

* [ ] {Jay McCarthy <jay.mccarthy@gmail.com>}
  - [ ] Web Server Tests
    ```
    raco test -c tests/web-server
    ```

  - [ ] XML Tests
    ```
    raco test -c tests/xml
    ```

  - [ ] HTML Tests
    ```
    raco test -c tests/html
    ```

  - [ ] PLAI Tests
    ```
    raco test -c plai
    ```

  - [ ] Racklog tests
    ```
    raco test -c racklog/tests
    ```

  - [ ] Datalog tests
    ```
    raco test -c datalog/tests
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

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests

