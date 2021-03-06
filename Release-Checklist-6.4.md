This page shows the state of testing for the 6.4 release. You may edit this page to check off your testing items when they or done, or you may email Ryan and he will update this page.

* [x] {Matthew Flatt <mflatt@cs.utah.edu>}
  - [x] Racket Tests
   ```
   racket -l tetsts/racket/test
   ```
  - [x] Languages Tests
   ```
   racket -l tests/htdp-lang/test-htdp
   ```
  - [x] GRacket Tests (Also check that `gracket -z` and `gracket-text`
        still work in Windows and Mac OS X)
   ```
   racket -l tests/gracket/test
   gracket -z
   gracket-text
   ```
  - [x] `mzc --exe` tests
   ```
   racket -l tests/compiler/embed/test
   ```
  - [x] .plt-packing Tests
   ```
   cd racket-test-core/tests/racket ; racket -f pack.rktl
   ```
  - [x] Games Tests
   ```
   plt-games
   ```
  - [x] R6RS Tests
   ```
   racket -l tests/r6rs/run.sps   # 3 failures expected
   ```
  - [x] PCPS test suite (in "pcps-test" repo)
   ```
   racket <file in pcps-test repo>
   ```
  - [x] Create an executable from a BSL program
   ```
   # make big-bang program with literal image in DrRacket, 
   # then create executable
   ```
  - [x] Run COM tests
   ```
   racket -l tests/racket/com
   ```
  - [x] Embed-in-c test
   ```
   racket -l tests/racket/embed-in-c
   ```
  - [x] Try compiling with `-funsigned-char`
   ```
   configure CPPFLAGS=-funsigned-char ; make
   ```
  - [x] Try compiling with `TEST_ALTERNATE_TARGET_REGISTER`
   ```
   configure CPPFLAGS=-DTEST_ALTERNATE_TARGET_REGISTER=1 ; make
   ```
  - [x] Run the unix installer tests (in "distro-build-test" package)
   ```
   racket -l tests/unix-installer <version>
   ```

  - [x] Updates:
    + [x] Racket Updates: update HISTORY (updates should show v`$RKTNVER` as the most current version)
    + [x] Update man pages in `racket/man/man1`: `racket.1`, `gracket.1`, `raco.1`
    + [x] Email me to pick the changes when they're done, or tell me if
          there are no such changes.

* [x] {Robby Findler <robby@eecs.northwestern.edu>}
  - [X] DrRacket Tests: 
   ```
   cd $(dirname $(raco fc tests/drracket/io)); ./run.sh
   ```
   
  - [X] Framework Tests:
   ```
   racket -l framework/tests/main
   ```

  - [x] Contracts Tests:
   ```
   racket -l tests/racket/contract/all
   racket -l tests/racket/contract-stress-argmin
   racket -l tests/racket/contract-stress-take-right
   ```

  - [x] Games Tests: play a bunch of games (not automated)
  - [x] Teachpacks Tests: image tests
    ```
    racket -l 2htdp/tests/bitmap-as-image-in-universe.rkt
    racket -l 2htdp/tests/image-equality-performance-htdp.rkt
    racket -l 2htdp/tests/image-equality-performance.rkt
    racket -l 2htdp/tests/image-too-large.rkt
    racket -l 2htdp/tests/test-image.rkt
   ```

  - [x] PLaneT Tests: 
   ```
   racket -l tests/planet/run-all ;; (the output of these tests is hard to read)
   ```
   
   - [x] Redex Tests:
   ```
   racket -l tests/redex/run-tests
   racket -l tests/redex/color-tests  ;; the results of this require interpretation
   ```

   - [X] Updates:
     +  DrRacket Updates: update HISTORY
     +  Redex Updates: update HISTORY (updates should show v`$RKTNVER` as the most current version)
     +  Ensure that previous version of DrRacket's preference files still starts up with new DrRacket
     +  Update man pages in `racket/man/man1`: `drracket.1`

* [X] {John Clements <clements@brinckerhoff.org>}
  - [X] Stepper Tests
  ```
  tests/stepper/run-manual-tests.rkt ;; run in DrRacket, ensure that expected failures occur.
  tests/stepper/manual-tests.txt ;; follow the instructions in this file
  ```

  - [X] Updates:
    + [X] Stepper Updates: update HISTORY

      (updates should show `v$RKTNVER` as the most current version; email
      me to pick the changes when they're done, or tell me if there
      are no such changes.)

* [x] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>, Vincent St-Amour <stamourv@ccs.neu.edu>}
  - [x] Match Tests:
  ```
  raco test -l tests/match/main
  ```
  
  - [x] Typed Racket Tests:
  ```
  racket -l typed-racket-test -- --all
  ```
  
  - [x] Typed Racket Updates: update HISTORY
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

* [x] {Ryan Culpepper <ryanc@ccs.neu.edu>}
  - [x] Macro Debugger Tests
  - [x] syntax-parse Tests
  - [x] RackUnit GUI Tests
  - [x] Data Tests
  - [x] DB Tests
  - [x] Rackunit Tests
  - [x] SRFI Tests
  - [x] Release tests for (one of the) linux releases:
    + [x] Test that the `racket` and `racket-textual` source releases
        compile fine (note that they're still called `plt` and `mz` at
        this stage).
    + [x] Test that the binary installers for both work, try each one in
        both normal and unix-style installation modes. (just ubuntu)
      [Note: get the release candidates from the URL in this email. Use
       the 'static table' link to see a list of all tar files available]

* [X] {Jay McCarthy <jay.mccarthy@gmail.com>}
  - [X] Web Server Tests
    ```
    raco test -c tests/web-server
    ```

  - [X] XML Tests
    ```
    raco test -c tests/xml
    ```

  - [X] HTML Tests
    ```
    raco test -c tests/html
    ```

  - [X] PLAI Tests
    ```
    raco test -c plai
    ```

  - [X] Racklog tests
    ```
    raco test -c racklog/tests
    ```

  - [X] Datalog tests
    ```
    raco test -c datalog/tests
    ```

* [x] {Stevie Strickland <sstrickl@ccs.neu.edu>}
  - [x] Unit Contract Tests
    ```
    raco test -l tests/units/test-unit-contracts
    ```

  - [x] Contract Region Tests
    ```
    racket tests/racket/contract/define-contract.rkt
    racket tests/racket/contract/with-contract.rkt
    ```

  - [x] Class Contract Tests
    ```
    racket tests/racket/contract/class.rkt
    ```

* [x] {Stephen Chang <stchang@ccs.neu.edu>}
  - [x] Lazy Racket Tests
    
    ```
    raco test -l lazy/tests/main.rkt
    ```
  - [x] Lazy stepper tests

    ```
    raco test -l tests/stepper/automatic-tests.rkt
    ```

* [ ] {Stephen Bloch <sbloch1964@gmail.com>}
  - [ ] Picturing Programs Tests

* [ ] {Greg Cooper <greg@cs.brown.edu>}
  - [ ] FrTime Tests

* [x] {Mike Sperber <sperber@deinprogramm.de>}
  - [x] DMdA Tests
    [Test properties](https://gist.github.com/mikesperber/51851dc0540307721c24),
    [World teachpack](https://gist.github.com/mikesperber/84273cd5d097edf1cf0f)
  - [x] Stepper Tests
    [Check format of lists, records](https://gist.github.com/mikesperber/47b614c59930c2fbc7f1)
  - [x] Signature Tests
    [Test signatures](https://gist.github.com/mikesperber/1ba48601a944ecb38309)

* [x] {David Van Horn <dvanhorn@ccs.neu.edu>}
  - [x] EoPL Tests

* [ ] {Neil Toronto <neil.toronto@gmail.com>}
  - [x] Plot Tests
  - [x] Images Tests
  - [x] Inspect icons
  - [ ] Math tests

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests