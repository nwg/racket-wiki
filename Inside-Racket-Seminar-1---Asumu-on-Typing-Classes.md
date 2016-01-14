Questions:
* Which parts of TR have a run-time dependency on the class type
checking? A compile-time dependency?

* What would be required to add support for `abstract` methods?

* What code exists that has to change because of the `super-new`
restriction? Does it fall into any simple patterns?

* Does the approach taken for class contracts make the system more
robust to changes in how `class` from `racket/class` is implemented
(by comparison to `match`, for example)?