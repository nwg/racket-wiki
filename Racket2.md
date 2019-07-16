

> Racket2 and syntax
> Jul 15Matthew Flatt
> tl;dr DON'T PANIC 

> At RacketCon today, after summarizing the state of work on Racket CS, I 
> recommended that we next explore the possibly of changing to an 
> infix-oriented syntax in "Racket2". 

> You can find the recording here: 

>  https://www.youtube.com/watch?v=dnz6y5U0tFs 

> Start at 32:27 for the part about what Racket2 could be. 

> I'll produce a text version of the rationale soon. For now, I'd like to 
> offer a few clarifications: 

>  * There is no specific proposal for a new syntax, yet. Our next step 
>    will be creating a process to explore a possible new syntax. 

>  * The talk does include some initial constraints that might guide the 
>    choice of a syntax. Even that meta level (i.e., the set of 
>    constraints) remains subject to a community process. 

>  * `#lang racket` is not going away and will always have its current 
>    parenthesis-oriented syntax. In the same way that Racket still 
>    supports `#lang scheme` and `#lang mzscheme` and even `(module 
>    <name> mzscheme ....)` and even top-level programs, the Racket 
>    compiler and runtime system will always support `#lang racket` 
>    programs. We believe that Racket's `#lang`-based ecosystem makes it 
>    uniquely positioned for trying new language variants while 
>    preserving and building on our past investments. 

>  * Any new syntax must specifically preserve Racket-style 
>    language-oriented programming, which means everything from defining 
>    simple pattern-based macros to building whole new `#lang`s with a 
>    smooth path in between. Again, our current macro technology must be 
>    an enabler for a new surface syntax, not a casualty. 

> As I hope comes across in the talk, I like the current Racket syntax 
> --- and how could I not, after 24 years of helping to define it? --- 
> and I am aware of many potential technical and social pitfalls that 
> this kind of shift could create. Still, in addition to keeping the core 
> Racket implementation running, I feel obliged to recommend changes that 
> I think would be good for the Racket language and community. We've been 
> lining up some technical solutions for a while. I don't know where the 
> community discussion will lead, but I'm pretty sure it's time to start 
> the conversation. 

> Whether or not we eventually decide on a different syntax, the design 
> of Racket2 will require community input and participation. If you want 
> to know more about how we're thinking about that process, see the 
> keynote by Aaron Turon: 

>       https://www.youtube.com/watch?v=xSjk2PdQm5k 

> (We'll have professionally edited videos of all talks available soon.) 

> Thanks, 
> Matthew 

* [DON’T PANIC](https://groups.google.com/d/msg/racket-users/3aIPOGbGgmc/A4HHSbdxAwAJ)
* [Racket2 RFC’s](https://github.com/racket/racket2-rfcs)

_Suggestion: sign and date any new entries_

***

A Wishlist of backwards incompatible things for a future Racket2.



**Note**: This is a wishlist. There's no guarantee any of these will be in a Racket2.

* Drop more guarantees about new object allocations: for example, allow `(append lst '())` to return `lst`,
  and the same for other list, string, bytes, vector functions (drop 0 items from the end of a list,
  `substring` and `regexp-replace` that don't change a string, etc).

* Remove `cond`'s default else-is-void clause and replace with a default else-is-error.

* Change `match` to recognize clauses based on bindings instead of symbols, and make
  it treat `else` like `cond`.

* Make every place where binding variables currently appear allow arbitrary match patterns (this requires some thought for handling what is currently things like `(define (f x) ..)`, so maybe we do this in a more limited way or change that way of defining functions to use a new keyword)

* Building on the match allowance, also allow functions to be defined case-by-case, for example maybe using a notation like this (roughly allowed in all internal definition contexts where `:=` is the keyword that triggers this kind of parsing):

        (length '()) := 0
        (length (cons x y)) := (+ 1 (len y))

And, even better, have this turn into `define/contract` or maybe `provide/contract` if something like this is written:

        length : (-> list? exact-nonnegative-integer?)
        (length '()) := 0
        (length (cons x y)) := (+ 1 (len y))

* Consider changing `cond` (and `match`) to use `#:else` instead of `else`.

* More prefabs for basic values, especially ones like srclocs where it is useful to make cross phase
  movements easy.

* Enable internal definitions everywhere.  (Note: this is tricky -- what's "everywhere"?
  Eg, can `define id` be followed by a definition(s) and then a value?  How about in the middle
  of an `if`?  Taken to an extreme, could definitions appear in an application form?)

* change syntax-case to allow internal definitions (possibly by getting rid of the 'guard' section)

* Enable the `define*` form (from `racket/package`) everywhere

* Use keywords in more places, such as unifying `member`, `memv`, `memf`, etc.

* Some syntax that avoids the verbosity in the `keyword-apply` etc kind of functions in the common
  case of passing keywords around.

* Some solution to the "no-value" value, which could be such a blessed value, or it could be a way
  to say that some function accepts all the keywords as some other function.  (Possibly related to
  the above, of course.)

* `struct` definition macro that allows
  - naming of the accessors/constructors/etc
  - ~~per-field `#:auto` values~~
  - ~~creating a constructor that takes all fields (when `#:auto` values should be something different)~~
  - ~~creating a constructor that makes `#:auto` fields optional keyword arguments~~
  - make `struct` have a function-like form that can specify auto values as optionals and/or keywords
  - maybe even allow several constructors with different argument "shapes"
  - more ideas from CL, like a `struct` keyword that actually use (tagged) lists for the values,
    similar to prefabs (and possibly redundant because of them)
  - like [sstruct2](https://github.com/jeapostrophe/exp/blob/master/sstruct2.rkt)

* Have only either `struct` or `define-struct`. Not both.

* Disallow mutation of `struct` bindings.

* include pattern matching forms in more binding positions (e.g. `define`, `let`/`for` clauses)

* Generic programming by default: `map`, `fold`, and friends are generic and not specialized to lists.

* Change `integer?` to mean `exact-integer?`.

* Get rid of the `arity-at-least` struct, and replace it with just an `arity` that abstracts over the
  whole arity thing -- always normalizing and includes keyword arity information.  Also, make it possible
  to always use a procedure where an arity is expected.

* Reconsider printing and equality of mutable and immutable variants of data types (vectors,
  hash tables, strings, etc.). Also reconsider the coercion of mutable vectors to immutable
  vectors by `datum->syntax`.

* Add CLOS-like defmethod (with multidispatch and :before, :after, :around) on Racket classes.

* Add interactive breakpoint in DrRacket debug. One should have REPL at breakpoint

* Make strings immutable.

* Have `with-output-to-string` and friends take a body, not a thunk. The current form is better named `call-with-output-to-string`, in the general pattern of `with-x` being syntax and `call-with-x` being a procedure.

* Have `<`, `>` and others take 0 or more arguments (returning `#t` for the 0 and 1 argument cases). This would allow applying them to lists without fear, which would allow patterns like `(define (sorted? l) (apply < l))`

* Rename `racket/cmdline` to `racket/command-line`.

* Require that macro literals always be bound.

* Make Matthew's doc-define from ClojureWest keynote real

* Consider having real identifiers for class/object members and use the module/namespace mechanisms to manage these references. Possibly in conjunction with a convention for names that are prefixed or included in others (so that we can have identifiers like `frame%:show` treated specially). Potentially makes method invocation faster and allows static detection of method-not-found errors.

* Have `quasiquote` support `...` as well as `,@`. Among other things, this lets `match` patterns can be like `match` "templates" (output expressions) and be like `syntax-case` etc.

* [tonyg] The .zo and .dep files should be invisible to the user. They should be created, deleted, invalidated, and processed generally without needing to form part of the user's mental model or workflow. Look at how python does this. It'd be lovely to make explicit calls to `raco make` (or even `raco setup`??) unnecessary.

* [jackfirth] Use syntax parameters in `for` loops for `break` and `continue` instead of keywords

* [alexis king] Make all of `match`’s patterns properly hygienic, rather than inspecting datums for the primitive pattern-matching constructs.

* [gus-massa] The values returned by `make-custom-hash-types` and `make-custom-set-types` have a different order. Change one of them to improve consistency.

* [sorawee] Mutable vector should be growable.

* [sdegabrielle] make regexes not need double escaping 