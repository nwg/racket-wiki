List of fixes/features for the planned Redex hackathon:
* multi-hole evaluation contexts
** being able to write up the pi-calculus in a natural way, with multi-hole contexts acting as congruence rules, could be a good goal here
* allow unquoting in judgment premise side-conditions
* cross-language metafunctions
* don't-bind-don't-care construct
* matching on more than just sexprs: structs, sets, hashes
** using this, incorporate some ideas from Jay's optimized Fedex system: (definition https://github.com/ericmercer/4M/blob/master/4M/super_model/fedex.rkt) (use https://github.com/ericmercer/4M/blob/master/4M/super_model/super-model.rkt) (uses structs to prevent duplicate checking of non-terminal matchedness, allows use to promise that there is only one deconstruction or one possible reduction) (I've found this can give 100x speed improvements.) 
* general "debugging" friendliness
** e.g. a "reasonable" means of introspecting the state of a reduction so that we don't have to e.g. put in nasty printing side-conditions
* disable caching for individual metafunctions (but not the metafunctions they call)
* "type-checking"-like thing for metafunctions: at the very least, every clause's pattern should have the same arity as the contract
** even better: check that the clause's pattern is a refined version of the pattern from the contract (this may be hard)
** "has some overlap with pattern contract" might be a more useful check
* shortcut arrows that are actually useful
** (There's already a macro hack by Ian for this; should be in redex-proper)
* a distinction between introducing a new variable and matching on that variable: would prevent trying to bind to that variable twice.
* 'traces' support for user-defined reduction relation applications (e.g. apply-reduction-relation*/random)
* built-in support for (partial/complete) hash and set matching.