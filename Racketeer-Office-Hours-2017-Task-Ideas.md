This is a list of suggestions for tasks to tackle during Racketeer Office Hours, if you didn't bring a project of your own to work on.

Most of these tasks should (modulo mistakes) be approachable by people who are new to contributing to Racket, possibly with some help from a current contributor to get started.

If you decide to work on one of these tasks, please edit this page to mark it as claimed by you, so we can avoid duplicate work. When you're done, you're welcome to post a link to the resulting pull request / commit / repo / etc.

# General Tasks
- Try to reproduce old bugs on gnats or github, close if they're not relevant anymore.

# Potential "Good first bugs"
moved to <https://github.com/racket/racket/wiki/Easy-bugs-to-fix>
# Automate more of the release tests

Using Docker for this, perhaps.

# Write a Slack bot in Racket

# Write new Typed Racket adapter modules

Some of these should go in `typed-racket-more`, some in their own packages. See http://docs.racket-lang.org/ts-reference/Libraries_Provided_With_Typed_Racket.html#%28part._.Porting_.Untyped_.Modules_to_.Typed_.Racket%29 for info about creating these.

* Write a checker for ensuring completeness of the TR docs on this
* `version/check`
* `version/patchlevel`
* `version/utils`
* `gregor`
* `data/ring-buffer`
* `tzinfo`
* `data/ddict` & `data/dset`
* `aws/*`

There are lots of other possibilities here.

# Try out Typed Racket with refinement types
 - see the `succeed/safe-vector.rkt` tests for some examples

# hash-lang lexer (find Ryan Davis)