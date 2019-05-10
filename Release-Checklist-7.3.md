# History Updates

* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
   - [ ] Updates:
     + [ ] Redex Updates: update HISTORY (updates should show v`7.3` as the most current version)
     + [ ] Update man pages in `racket/man/man1`: `drracket.1`

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show v7.3 as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)


# Testing

* [ ] {Blockers}

* [ ] {Robby Findler <robby@eecs.northwestern.edu>}
   + [ ] Ensure that previous version of DrRacket's preference files still starts up with new DrRacket

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

* [ ] {Doug Williams <m.douglas.williams@gmail.com>}
  - [ ] Additional Plot Tests
