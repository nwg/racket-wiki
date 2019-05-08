# History Updates

* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
   - [ ] Updates:
     + [ ] DrRacket Updates: update HISTORY
     + [ ] Redex Updates: update HISTORY (updates should show v`7.3` as the most current version)
     + [ ] Update man pages in `racket/man/man1`: `drracket.1`

* [ ] {John Clements <clements@brinckerhoff.org>}
  - [ ] Updates:
    + [ ] Stepper Updates: update HISTORY
      (updates should show `v7.3` as the most current version; email
      me to pick the changes when they're done, or tell me if there
      are no such changes.)

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show v7.3 as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

* [ ] {Matthias Felleisen <matthias@ccs.neu.edu>}
  - [ ] Updates:
    + [ ] Teachpack Updates: update HISTORY
      (updates should show `v7.3` as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

# Testing

* [ ] {Blockers}

* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
  - [ ] DrRacket Tests: 
   + [ ] Ensure that previous version of DrRacket's preference files still starts up with new DrRacket
     
  - [ ] Release tests for the Windows release:
    + [ ] Test that the `racket-minimal` source release compiles fine.
    + [ ] Test that the binary installers for both work.

* [ ] {John Clements <clements@brinckerhoff.org>}
  - [ ] Stepper Tests
  ```
  tests/stepper/run-manual-tests.rkt ;; run in DrRacket, ensure that expected failures occur.
  tests/stepper/manual-tests.txt ;; follow the instructions in this file
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

* [ ] {John Clements <clements@racket-lang.org>}
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

* [X] {Mike Sperber <sperber@deinprogramm.de>}
  - [X] DMdA Tests
    [Test properties](https://gist.github.com/mikesperber/51851dc0540307721c24),
    [World teachpack](https://gist.github.com/mikesperber/84273cd5d097edf1cf0f)
  - [X] Stepper Tests
    [Check format of lists, records](https://gist.github.com/mikesperber/47b614c59930c2fbc7f1)
  - [X] Signature Tests
    [Test signatures](https://gist.github.com/mikesperber/1ba48601a944ecb38309)

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests


* [x] {Spencer Florence <spencer.florence@eecs.northwestern.edu>}
  - [x] Pict Tests. Uncomment the tests disabled [here](https://github.com/racket/pict/commit/eec716eabe1018226cb674f672388f1f709c6423) then

    ```
    raco test -p pict pict-lib pict-doc pict-test
    ```