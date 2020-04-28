Although github has a nifty syntax for checking the boxes below, you should probably just go ahead and delete the items, rather than check them off; it's much easier to see what remains to be done when everything else is simply not there.

# History Updates

* [ ] {John Clements <clements@racket-lang.org>}
  - [ ] Updates:
    + [ ] Stepper Updates: update HISTORY
      (updates should show `v7.7` as the most current version; include
      the text "merge" in the commit message, or tell me if there
      are no such changes.)

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show `v7.7` as the most current version; include
      the text "merge" in the commit message, or tell me if there 
      are no such changes.)

* [ ] {Matthias Felleisen <matthias@ccs.neu.edu>}
  - [ ] Updates:
    + [ ] Teachpack Updates: update HISTORY
      (updates should show `v7.7` as the most current version; include
      the text "merge" in the commit message, or tell me if there are no such
      changes.)

# Testing


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

  - [ ] Test #lang htdp/* languages

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
  - [ ] Stepper Tests
   ```
   tests/stepper/run-manual-tests.rkt ;; run in DrRacket, ensure that expected failures occur.
   tests/stepper/manual-tests.txt ;; follow the instructions in this file
   ```
  - [ ] Release tests for (a chosen) linux release and the Mac OS release:
    + [ ] Test that the `racket` source release compiles on linux
    + [ ] Test that the `racket-minimal` source release compiles on linux
    + [ ] Test that the binary installer for linux works in normal mode (install
          then start racket) [FIXME: is this enough?]
    + [ ] Test that the binary installer for linux works in unix-style mode
          (install then start racket) [FIXME: is this enough?]
  - [ ] Release tests for the Mac OS release:
    + [ ] On MacOS: Build from sources using the minimal distribution:
      ```
      cd src
      mkdir build
      cd build
      ../configure
      make
      make install
      ```

      then

      ```
      ./bin/raco pkg install --auto -i racket-lib
      ./bin/raco pkg install --auto -i main-distribution
      ```
      
      (Why not just test the full source release? 
          "The problem is that when packages are already included in a source
          bundle, then it doesn't include the right versions of packages that
          have to be platform-specific, such as the one that supplies
          "libintl.9.dylib".)
    + [ ] Test that the binary installer for MacOS works (install, start DrRacket)
  - [ ] FrTime Tests (in frtime/demos)
    + [ ] Test that expressions with time-varying values (e.g., `seconds`,
        `(build-list (modulo seconds 10) identity)`) render and update as
        expected in the FrTime language level. Check that they continue
        updating even after a garbage collection.
    + [ ] Test that a sampling of graphical demos (e.g., `analog-clock.rkt`,
        `tetris.rkt`) work as expected, responding to relevant key and mouse
        events and interactions with control widgets.
  - [ ] Inspect icons
    ```
    raco docs icons # then look at them (look for icons, ensure no red error text on the page)
    ```

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

* [ ] {Spencer Florence <spencer.florence@eecs.northwestern.edu>}
  - [ ] Pict Tests. Uncomment the tests disabled [here](https://github.com/racket/pict/commit/eec716eabe1018226cb674f672388f1f709c6423) then

    ```
    raco test -p pict pict-lib pict-doc pict-test
    ```