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
   cd $(dirname $(raco fc tests/drracket/io)); ./run.sh
   ```
   
  - [ ] Framework Tests:
   ```
   racket -l framework/tests/main
   ```

  - [ ] Contracts Tests:
   ```
   racket -l tests/racket/contract/all
   racket -l tests/racket/contract-opt-tests.rkt
   racket -l tests/racket/contract-rand-test.rkt
   racket -l tests/racket/contract-stress-argmin.rkt
   racket -l tests/racket/contract-stress-take-right.rkt
   ```

  - [ ] Games Tests: play a bunch of games (not automated)
  - [ ] Teachpacks Tests: image tests
    ```
    racket -l 2htdp/tests/bitmap-as-image-in-universe.rkt
    racket -l 2htdp/tests/image-equality-performance-htdp.rkt
    racket -l 2htdp/tests/image-equality-performance.rkt
    racket -l 2htdp/tests/image-too-large.rkt
    racket -l 2htdp/tests/test-image.rkt
   ```

  - [ ] PLaneT Tests: 
   ```
   racket -l tests/planet/run-all ;; (the output of these tests is hard to read)
   ```
   
   - [ ] Redex Tests:
   ```
   racket -l tests/redex/run-tests
   racket -l tests/redex/color-tests  ;; the results of this require interpretation
   ```

   - [ ] Updates:
     + [ ] DrRacket Updates: update HISTORY
     + [ ] Redex Updates: update HISTORY (updates should show v`$RKTNVER` as the most current version)
     + [ ] Ensure that previous version of DrRacket's preference files still starts up with new DrRacket
     + [ ] Update man pages in `racket/man/man1`: `drracket.1`
     + [ ] Email me to pick the changes when they're done, or tell me if there are no such changes.

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
  raco test -l tests/match/plt-match-tests
  ```
  
  - [ ] Typed Racket Tests:
  ```
  racket -l typed-racket-test/run -- --all
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

* [ ] {Ryan Culpepper <ryanc@ccs.neu.edu>}
  - [ ] Macro Debugger Tests
  - [ ] syntax-parse Tests
  - [ ] RackUnit GUI Tests
  - [ ] Data Tests
  - [ ] DB Tests
  - [ ] Rackunit Tests
  - [ ] SRFI Tests
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
    raco test -c tests/racklog
    ```

  - [ ] Datalog tests
    ```
    raco test -c tests/datalog
    ```

* [ ] {Stevie Strickland <sstrickl@ccs.neu.edu>}
  - [ ] Unit Contract Tests
    ```
    raco test -l tests/units/test-unit-contracts
    ```
  - [ ] Contract Region Tests
  - [ ] Class Contract Tests

* [ ] {Stephen Chang <stchang@ccs.neu.edu>}
  - [ ] Lazy Racket Tests
  - [ ] Lazy stepper tests

* [ ] {Stephen Bloch <sbloch@adelphi.edu>}
  - [ ] Picturing Programs Tests

* [ ] {Greg Cooper <greg@cs.brown.edu>}
  - [ ] FrTime Tests

* [ ] {Mike Sperber <sperber@deinprogramm.de>}
  - [ ] DMdA Tests
  - [ ] Stepper Tests
  - [ ] Signature Tests

* [ ] {David Van Horn <dvanhorn@ccs.neu.edu>}
  - [ ] EoPL Tests

* [ ] {Neil Toronto <neil.toronto@gmail.com>}
  - [ ] Plot Tests
  - [ ] Images Tests
  - [ ] Inspect icons
  - [ ] Math tests

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests

* [ ] {Shriram Krishnamurthi <sk@cs.brown.edu>}
  - [ ] Tour: check the tour and generate a new one if needed.
      [Note: Since this is a `v$RKTAVER` build, you will need to edit your
        `.../collects/framework/private/version.rkt`
      file and change `(version)` to `"$RKTNVER"`.]
