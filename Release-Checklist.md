This is the master copy of the history updates and testing checklist for Racket releases. Edit this version to add testing responsibilities or to include the commands used to run listed tests.

A copy of this checklist for the current release in progress is at [[Release-Checklist-7.7]]. That page is edited when testing items are completed.

Although github has a nifty syntax for checking the boxes below, you should probably just go ahead and delete the items, rather than check them off; it's much easier to see what remains to be done when everything else is simply not there.

# History Updates

* [ ] {Matthew Flatt <mflatt@cs.utah.edu>}
  - [ ] Updates:
    + [ ] Racket Updates: update HISTORY (updates should show `v$RKTNVER` as the most current version)
    + [ ] Update man pages in `racket/man/man1`: `racket.1`, `gracket.1`, `raco.1`

* [ ] {Robby Findler <robby@cs.northwestern.edu>}
   - [ ] Updates:
     + [ ] DrRacket Updates: update HISTORY
     + [ ] Redex Updates: update HISTORY (updates should show `v$RKTNVER` as the most current version)
     + [ ] Update man pages in `racket/man/man1`: `drracket.1`

* [ ] {John Clements <clements@racket-lang.org>}
  - [ ] Updates:
    + [ ] Stepper Updates: update HISTORY
      (updates should show `v$RKTNVER` as the most current version; include
      the text "merge" in the commit message, or tell me if there
      are no such changes.)

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show `v$RKTNVER` as the most current version; include
      the text "merge" in the commit message, or tell me if there 
      are no such changes.)

* [ ] {Matthias Felleisen <matthias@ccs.neu.edu>}
  - [ ] Updates:
    + [ ] Teachpack Updates: update HISTORY
      (updates should show `v$RKTNVER` as the most current version; include
      the text "merge" in the commit message, or tell me if there are no such
      changes.)

# Testing

* [ ] {Blockers}

* [ ] {Matthew Flatt <mflatt@cs.utah.edu>}
  - [ ] Racket Tests
   ```
   racket -l tests/racket/test
   ```
  - [ ] Languages Tests
   ```
   racket -l tests/htdp-lang/test-htdp
   ```
  - [ ] GRacket Tests (Also check that `gracket -z` and `gracket-text`
        still work in Windows and Mac OS X)
   ```
   racket -l tests/gracket/test
   gracket -z
   gracket-text
   ```
  - [ ] `mzc --exe` tests
   ```
   racket -l tests/compiler/embed/test
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
  - [ ] Try creating a BSL sandbox in DrRacket
   ```
   (require racket/sandbox)
   (define e (make-evaluator 'lang/htdp-beginner))
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

* [ ] {Robby Findler <robby@cs.northwestern.edu>}
  - [ ] DrRacket Tests: 
   ```
   # from the top-level directory of the release bundle, run
   cd "$(dirname "$(./bin/racket -e '(display (collection-file-path "io.rkt" "tests" "drracket"))')")"
   chmod +x ./run.sh
   # adjust the RACKET environment variable to point to the right binary, eg:
   env RACKET=~/Desktop/Racket\ v6.3.90.900/bin/racket ./run.sh
   ```
   + [ ] Ensure that previous version of DrRacket's preference files still starts up with new DrRacket
     
  - [ ] Framework Tests:
   ```
   # from the top-level directory of the release bundle, run
   cd "$(dirname "$(./bin/racket -e '(display (collection-file-path "main.rkt" "framework" "tests"))')")"
   raco test .
   ```

  - [ ] Contracts Tests:
   ```
   racket -l tests/racket/contract/all
   racket -l tests/racket/contract-stress-argmin
   racket -l tests/racket/contract-stress-take-right
   ```

  - [ ] Games Tests: play a bunch of games (not automated)
  - [ ] Teachpacks Tests: image tests
   ```
   racket -l 2htdp/tests/bitmap-as-image-in-universe
   racket -l 2htdp/tests/image-equality-performance-htdp
   racket -l 2htdp/tests/image-equality-performance
   racket -l 2htdp/tests/image-too-large
   racket -l 2htdp/tests/test-image
   ```

  - [ ] PLaneT Tests: 
   ```
   # (the output of these tests is hard to read)
   raco test -l tests/planet/run-all
   ```
   
   - [ ] Redex Tests:
   ```
   racket -l redex/tests/run-tests
   # the results of color-tests require interpretation (and clicking)
   racket -l redex/tests/color-tests 
   ```

  - [ ] Release tests for the Windows release:
    + [ ] Test that the `racket-minimal` source release compiles fine; follow the instructions in `src/README`.
    + [ ] Test that the binary installers for both work.

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Match Tests:
  ```
  raco test -l tests/match/main
  ```
  
  - [ ] Typed Racket Tests:
  ```
  racket -l typed-racket-test -- --all
  ```

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

  - [ ] EoPL Tests
    ```
    raco test -c eopl/tests
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
  - [ ] DMdA Tests
    [Test properties](https://gist.github.com/mikesperber/51851dc0540307721c24),
    [World teachpack](https://gist.github.com/mikesperber/84273cd5d097edf1cf0f)
  - [ ] Stepper Tests
    [Check format of lists, records](https://gist.github.com/mikesperber/47b614c59930c2fbc7f1)
  - [ ] Signature Tests
    [Test signatures](https://gist.github.com/mikesperber/1ba48601a944ecb38309)

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests

* [ ] {Spencer Florence <spencer.florence@eecs.northwestern.edu>}
  - [ ] Pict Tests. Uncomment the tests disabled [here](https://github.com/racket/pict/commit/eec716eabe1018226cb674f672388f1f709c6423) then

    ```
    raco test -p pict pict-lib pict-doc pict-test
    ```