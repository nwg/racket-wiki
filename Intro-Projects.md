This page lists Racket projects which are feasible for people who don't have a lot of experience with the Racket code base. They're mostly small, self contained, and would be extremely useful. Some involve writing a new library that would be useful to lots of other people, and some help fix or clean up some aspect of the existing Racket code base.  

The best place to ask for help with any of these is on the [users mailing list](http://racket-lang.org/community.html).  

# Code Improvements

These are improvements to the Racket source.  Fork the GitHub repository and then submit a pull request.

* Revise the FFI docs
* Etags support for Racket features
* Port code that uses `class100` to the current class system
* Get rid of units in the net collect
* Extend the gabot IRC bot to deliver messages to offline people (contact Eli for more info)
* Racket support for github code highlighting
* Racket support for github code editing
* Fix warnings in C code
* Find uses of a-lists and replace them with hash tables
* Find things that use lists for sets, replace them with `racket/set'
* Find uses of srfi/1, replace them with racket/list stuff
* Documentation clarifications and/or small examples
* Add support for macro-debugger/analysis/check-requires to xrepl

# Small Projects

These are self-contained projects.  Just create a new github repository, and start hacking.  When you have something that works, release it on [PLaneT](http://planet.racket-lang.org).  

* Write bindings for libgit
* Write libraries to interact with Wii Remotes
* Write libraries to interact with game controllers
* Write bindings to the Google APIs
* Write bindings to the Github API
* Write bindings to the Twitter APIs
* Write bindings to the Facebook APIs
* Write bindings to Amazon AWS
* Write XMPP bindings
* Bindings for a text to speech engine
* IRC client library
* IRC log highlighter
* Bindings for Apple's Core * Libraries
* Write better s-exp diff tool
* Write bindings to gobject introspection
* Improve Racket support in Ohloh's line counter

# Larger Projects

For the more ambitious Racketeer ...

* Write a markdown parser
* Write a YAML parser
* Write a gitolite replacement in Racket
* #lang scsh
* Write a blogging framework
* Write a Common Lisp compatibility layer
* Write a Clojure compatibility layer
* Fix Swindle to have call-next-method available without #lang swindle

