# History Updates

* [ ] {Sam Tobin-Hochstadt <samth@ccs.neu.edu>}
  - [ ] Typed Racket Updates: update HISTORY
      (updates should show v7.0 as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

* [ ] {Matthias Felleisen <matthias@ccs.neu.edu>}
  - [ ] Updates:
    + [ ] Teachpack Updates: update HISTORY
      (updates should show v7.0 as the most current version; email me
      to pick the changes when they're done, or tell me if there are no such
      changes.)

# Testing

* [ ] {Blockers}
  - https://github.com/racket/racket/issues/2099     

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