These are improvements to the Racket source.  Fork the GitHub repository
and then submit a pull request. For detailed guidance see [[Contributing to Racket]].

* Find uses of alists and replace them with hash tables where
  appropriate (note that short alists, below ~40 items, can be faster than hashes)
  - Search for uses of `assq` and friends to find
* Find things that use lists for sets, replace them with `racket/set`
  - Search for uses of `member` and friends to find
* Find uses of `srfi/1`, replace them with `racket/list` stuff
* Fix Swindle to have `call-next-method` available without `#lang swindle`
* Find uses of log-xxx (using the global logger), and use 5.3.2's new `define-logger` form to change them to use their own logger. That way, users can filter the log messages. Examples might include "optimizer" and "file dependency" categories of messages.
* Fix warnings in C code  _(Forked to pmatos/racket to sort this one out. Will issue pull request when completed.)_
  - Refer to the nightly build [logs](http://pre.racket-lang.org/build-log.txt) for our distributed platforms

## Other ways to contribute
 * [[Integration Projects]] These are improvements to other systems to better support Racket.
 * [[Documentation Improvements]] has ideas where you can help improve the documentation

## Completed Code Improvements
* ~~Add support for `macro-debugger/analysis/check-requires` to xrepl~~ (Completed by Eli)
* ~~Port code that uses `class100` to the current class system~~ _(Completed by Asumu)_
* ~~Get rid of units in the net collect~~ _(Done by Jon Zeppieri)_