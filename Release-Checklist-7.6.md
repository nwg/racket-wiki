
# History Updates

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show `v7.6` as the most current version; include
      the text "merge" in the commit message, or tell me if there 
      are no such changes.)

# Testing

* [ ] {Blockers}


* [ ] {John Clements <clements@racket-lang.org>}
  - [ ] Stepper Tests
   ```
   tests/stepper/run-manual-tests.rkt ;; run in DrRacket, ensure that expected failures occur.
   tests/stepper/manual-tests.txt ;; follow the instructions in this file
   ```
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
    raco docs icons # then look at them (look for icons, ensure no red error text on the page)
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

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests

* [ ] {Spencer Florence <spencer.florence@eecs.northwestern.edu>}
  - [ ] Pict Tests. Uncomment the tests disabled [here](https://github.com/racket/pict/commit/eec716eabe1018226cb674f672388f1f709c6423) then

    ```
    raco test -p pict pict-lib pict-doc pict-test
    ```
