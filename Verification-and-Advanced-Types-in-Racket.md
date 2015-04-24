Typed Racket is cool and a lot of us are interested in bringing Racket closer to things like Coq and doing other sorts of theorem proving and advanced verification. Please list your project here, so we can find out about each other, to de-duplicate work and stay in contact.

* Jay McCarthy wants to do to Racket what Agda/Idris did to Haskell relative to Coq, including making awesome macros and extracting to normal (or Typed) Racket with beautiful contracts.

* Andrew Kent (andmkent@indiana.edu) is interested in this topic generally. Thus far he has looked at adding incremental packages/features to Racket that allow users to enforce more guarantees statically. Examples include:
    1. An algebraic datatypes package (only Typed Racket support at the moment). [pkg](http://pkgs.racket-lang.org/#[datatype]) 
    2. Adding refinements and linear constraints to Typed Racket (in-progress). [repo](https://github.com/andmkent/typed-racket)

* Phil Nguyen, David Van Horn, and Sam Tobin-Hochstadt want to verify contracts statically, giving them many of the benefits of refinement type systems, without the shortcomings of all-or-nothing verification methods.  We're currently working on extending our implementation to work on real Racket code after macro expansion.

* William J. Bowman is interested in how advanced meta-programming can benefit dependently-typed languages and theorem proving. He has implemented [Cur](https://github.com/bluephoenix47/cur), a dependently-typed language over which Racket macros can operate.

* Prabhakar Ragde has worked with and taught using both Racket and Coq, and is interested in bridging the gap between them.
