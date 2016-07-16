Release blockers:
* [ ] resolve the TR `any-wrap/c` issue

* [ ] {Matthew Flatt <mflatt@cs.utah.edu>}
  - [ ] Racket Tests
   ```
   racket -l tetsts/racket/test
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
   cd racket-test-core/tests/racket ; racket -f pack.rktl
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
   racket -l tests/unix-installer <version>
   ```

  - [ ] Updates:
    + [ ] Racket Updates: update HISTORY (updates should show v`$RKTNVER` as the most current version)
    + [ ] Update man pages in `racket/man/man1`: `racket.1`, `gracket.1`, `raco.1`
    + [ ] Email me to pick the changes when they're done, or tell me if
          there are no such changes.

* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
  - [ ] DrRacket Tests: 
   ```
   # from the top-level directory of the release bundle, run
   cd "$(dirname "$(./bin/racket -e '(display (collection-file-path "io.rkt" "tests" "drracket"))')")"
   chmod +x ./run.sh
   # adjust the RACKET environment variable to point to the right binary, eg:
   env RACKET=~/Desktop/Racket\ v6.3.90.900/bin/racket ./run.sh
   ```
   
  - [ ] Framework Tests:
   ```
   racket -l framework/tests/main
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

* [ ] {Ryan Culpepper <ryanc@ccs.neu.edu>}
  - [ ] Macro Debugger Tests
    ```
    racket -l tests/macro-debugger/all-tests.rkt -- --gui
    ```

  - [x] syntax-parse Tests
    ```
    raco test -c tests/stxparse
    ```

  - [x] RackUnit GUI Tests
    ```
    # not automated
    ```

  - [x] Data Tests
    ```
    raco test -c tests/data
    ```

  - [x] DB Tests
    ```
    # basic tests with sqlite3; other tests require local software & configuration
    racket -l tests/db/all-tests
    ```

  - [x] Rackunit Tests
    ```
    # note: some tests are intended to fail
    racket -l tests/rackunit/run-tests
    ```

  - [x] SRFI Tests
    ```
    racket -l tests/srfi/run-tests
    ```

  - [ ] Release tests for (one of the) linux releases:
    + [ ] Test that the `racket` and `racket-minimal` source releases
        compile fine.
    + [ ] Test that the binary installers for both work, try each one in
        both normal and unix-style installation modes.

* [x] {Jay McCarthy <jay.mccarthy@gmail.com>}
  - [x] Web Server Tests
    ```
    raco test -c tests/web-server
    ```

  - [x] XML Tests
    ```
    raco test -c tests/xml
    ```

  - [x] HTML Tests
    ```
    raco test -c tests/html
    ```

  - [x] PLAI Tests
    ```
    raco test -c plai
    ```

  - [x] Racklog tests
    ```
    raco test -c racklog/tests
    ```

  - [x] Datalog tests
    ```
    raco test -c datalog/tests
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

