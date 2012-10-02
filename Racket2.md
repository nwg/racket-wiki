A wishlist of backwards incompatible things for a future Racket2.

* Remove cond's default else-is-void clause and replace with a default else-is-error

* Enable internal definitions everywhere
* Enable the racket/package define* form everywhere
* Use keywords in more places, such as unifying member, memv, memf, etc.
* struct definition macro that allows
  - naming of the accessors/constructors/etc
  - per-field #:auto values
  - creating a constructor that takes all fields (when #:auto values should be something different)
  - creating a constructor that makes #:auto fields optional keyword arguments
* include pattern matching forms in more binding positions (e.g. for clauses, define)

