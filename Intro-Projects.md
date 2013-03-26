This page lists [Racket](http://www.racket-lang.org) projects which are feasible for people who don't
have a lot of experience with the Racket code base. They're mostly
small, self contained, and would be extremely useful. Some involve
writing a new library that would be useful to lots of other people, and
some help fix or clean up some aspect of the existing Racket code base.

The best place to ask for help with any of these is on the [users
mailing list](http://racket-lang.org/community.html).

# Small Projects

These are self-contained projects.  Just create a new github repository,
and start hacking.  When you have something that works, release it on
[PLaneT](http://planet.racket-lang.org).

* Implement a Rosetta code task: http://rosettacode.org/wiki/Reports:Tasks_not_implemented_in_Racket
* Data structures: [hash array mapped trie](http://en.wikipedia.org/wiki/Hash_array_mapped_trie), [2-3 finger trees](http://en.wikipedia.org/wiki/Finger_tree), other [purely functional data structures](http://cstheory.stackexchange.com/questions/1539/whats-new-in-purely-functional-data-structures-since-okasaki) (some already implemented [here](https://github.com/takikawa/tr-pfds)).
* Code for doing OAuth
  - Now available [here](https://github.com/veer-public/OAuth-2.0)
  - Also available as part of ryanc's webapi PLaneT package.
* Write bindings for libgit
  - Work started [here](https://github.com/jarnaldich/racket-git)
* Write bindings to Authorize.Net
* Write libraries to interact with Wii Remotes
  - [Technical details](http://wiibrew.org/wiki/Wiimote) on the Wiimote
  - [wiiuse](http://sourceforge.net/projects/wiiuse/) has code for the Wiimote's protocol, as well as Win/Linux bluetooth code
  - Mac OSX [Bluetooth Dev info](http://developer.apple.com/library/mac/#documentation/DeviceDrivers/Conceptual/Bluetooth/BT_Intro/BT_Intro.html)
* Write libraries to interact with game controllers
  - This exists on for [Mac OS X](https://github.com/get-bonus/get-bonus/blob/master/exp/joystick.rkt), but an interface should be normalized and available across platforms.
  - maybe use [libsdl](http://www.libsdl.org/)?
* Write bindings to various Google APIs
  - Authentication would be useful
  - Other interesting things: docs (esp. around spreadsheets), maps
* Write bindings to the Github API
* Write bindings to the Twitter APIs
* Write bindings to the Facebook APIs
* Write bindings to Amazon AWS.
  - [Eric Hanchrow](https://github.com/offby1/doodles/tree/master/plt-scheme/web/amazon) has some pitiful first steps which might be inspirational.
  - Staying in the pitiful vein, a typed/racket effort by [Ray Racine](https://github.com/RayRacine/knozamalib/tree/master/src/racket/aws) which is actively being developed.
  - Greg Hendershott has untyped Racket code for the S3, SDB, SES, SNS, SQS, and CloudWatch services: [PLaneT package](http://planet.racket-lang.org/display.ss?package=aws.plt&owner=gh), [Github](https://github.com/greghendershott/aws). 
* Write XMPP bindings
   - A starting point can be found [here](https://github.com/zzkt/gibberish)
* Bindings for a text to speech engine
* IRC log highlighter
* IRC client library (can be based on the gabot code (contact [Eli](mailto:eli@barzilay.org)), which
  is better for a library than [rudybot](https://github.com/offby1/rudybot))
* Bindings for Apple's Core-* Libraries
* Write a better s-exp diff tool
* Write bindings to gobject introspection

# Code Improvements

These are improvements to the Racket source.  Fork the GitHub repository
and then submit a pull request.

* ~~Port code that uses `class100` to the current class system~~ _(Completed by Asumu)_
* ~~Get rid of units in the net collect~~ _(Done by Jon Zeppieri)_
* Fix warnings in C code  _(Forked to pmatos/racket to sort this one out. Will issue pull request when completed.)_
  - Refer to the nightly build [logs](http://pre.racket-lang.org/build-log.txt) for our distributed platforms
* Find uses of alists and replace them with hash tables where
  appropriate (note that short alists, below ~40 items, can be faster than hashes)
  - Search for uses of `assq` and friends to find
* Find things that use lists for sets, replace them with `racket/set`
  - Search for uses of `member` and friends to find
* Find uses of `srfi/1`, replace them with `racket/list` stuff
* ~~Add support for `macro-debugger/analysis/check-requires` to xrepl~~ (Completed by Eli)
* Fix Swindle to have `call-next-method` available without `#lang swindle`
* Find uses of log-xxx (using the global logger), and use 5.3.2's new `define-logger` form to change them to use their own logger. That way, users can filter the log messages. Examples might include "optimizer" and "file dependency" categories of messages.

# Documentation Improvements

Similar to code improvements (docs are code).

* Revise the FFI docs: better docs, lots of examples, guide-like text
* Add a detailed example to the profiler manual.
* Documentation clarifications and/or small examples
* Write tutorials for building small applications and using major features, e.g., the class system or macros.
* Convert Eli's Swindle documentation to Scribble.

# Integration

These are improvements to other systems to better support Racket.

* Racket support for github code highlighting
  - In progress: Github (and Bitbucket) use [pygments](http://pygments.org/docs/lexerdevelopment/). Gave pygments a [pull request](https://bitbucket.org/birkenfeld/pygments-main/pull-request/94/add-lexer-for-racket-language) to use a new `RacketLexer` instead of `SchemeLexer`. Accepted and merged into pygments 2012-08-23. Waiting for Github and Bitbucket to pull latest pygments.
* Racket support for github code editing
* Etags support for Racket features
* Improve Racket support in Ohloh's line counter
* Racket support in MediaWiki's GeSHi highligher
* Extend the gabot IRC bot to deliver messages to offline people
  (contact [Eli](mailto:eli@barzilay.org) for more info)
  - Optionally, extend it to do more cool stuffs
  - [rudybot](https://github.com/offby1/rudybot) is another possible starting point

# Larger Projects

For the more ambitious Racketeer ...

* Write a markdown parser (important: lots of tests; support at least
  popular variants that are used by stackoverflow and github)
  - [Norman Gray](http://nxg.me.uk) has a WikiCreole parser [on PLaneT](http://planet.racket-lang.org/display.ss?package=squicky.plt&owner=nxg).  It's reasonably clear how to generalise that to cope with markdown, and Norman is working on this as a background project.
  - Also available [here](https://github.com/greghendershott/markdown).
* Write a YAML parser
  - Now available [on PLaneT](http://planet.racket-lang.org/display.ss?package=yaml.plt&owner=esilkensen).
* Write a gitolite replacement in Racket (contact [Eli](mailto:eli@barzilay.org))
* `#lang scsh` -- or better: write just a library for similar bindings
  (macros & functions), and make it into a language that has shell-like
  syntax
* Write a blogging framework
* Write a Common Lisp compatibility layer (same functionality, but not
  all the core language features that would make this extremely
  difficult; for example: keep immutable pairs)
* Write a Clojure compatibility layer
  - Started on one [here](https://github.com/takikawa/racket-clojure) but it needs a lot more work.
* Write bindings to SDL (note that there are Allegro bindings on planet).
* Integrate the existing parser-tools [SRE](http://www.ccs.neu.edu/home/shivers/papers/sre.txt) with Racket regexps.
* Write some code metrics tools (number of functions, number of lines, etc) and integrate them with DrRacket's module browser.