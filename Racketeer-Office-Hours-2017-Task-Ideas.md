This is a list of suggestions for tasks to tackle during Racketeer Office Hours, if you didn't bring a project of your own to work on.

Most of these tasks should (modulo mistakes) be approachable by people who are new to contributing to Racket, possibly with some help from a current contributor to get started.

If you decide to work on one of these tasks, please edit this page to mark it as claimed by you, so we can avoid duplicate work. When you're done, you're welcome to post a link to the resulting pull request / commit / repo / etc.

# General Tasks
- Tag packages on pkgs.racket-lang.org, and/or add missing descriptions.
  And if feeling bold, add docs, or convert docs in other formats, if they exist.
- Add a localization for a language you know.
- Try to reproduce old bugs on gnats or github, close if they're not relevant anymore.

# Docs that could use examples
- Racket reference (claim one section at a time. 4 has a number of functions with examples missing, but others probably do too)
- syntax
- racket/draw
- racket/gui & framework (with screenshots) (claim one section at a time)
- scribble, low-level API section
- graphics/turtles & graphics/value-turtles
- string-constants
- syntax-color (not exactly easy to use, examples could really help)
- openssl (make-log-based-evaluator can help here)
- net (claim one section at a time)
- racket/unix-socket
- parser-tools
- file (claim one section at a time)
- data (claim one section at a time)

# Potential "Good first bugs"
- [https://github.com/racket/racket/issues/1740](https://github.com/racket/racket/issues/1740)
- [https://github.com/racket/racket/issues/1699](https://github.com/racket/racket/issues/1699)
- [https://github.com/racket/racket/issues/1690](https://github.com/racket/racket/issues/1690) (most of the way there, mostly integration remains)
- [https://github.com/racket/racket/issues/1683](https://github.com/racket/racket/issues/1683)
- [https://github.com/racket/racket/issues/1654](https://github.com/racket/racket/issues/1654)
- [https://github.com/racket/racket/issues/1653](https://github.com/racket/racket/issues/1653)
- [https://github.com/racket/racket/issues/1637](https://github.com/racket/racket/issues/1637)
- [https://github.com/racket/racket/issues/1636](https://github.com/racket/racket/issues/1636)
- [https://github.com/racket/racket/issues/1629](https://github.com/racket/racket/issues/1629) (goes with the next 2)
- [https://github.com/racket/racket/issues/1628](https://github.com/racket/racket/issues/1628)
- [https://github.com/racket/racket/issues/1627](https://github.com/racket/racket/issues/1627)
- [https://github.com/racket/racket/issues/1615](https://github.com/racket/racket/issues/1615)
- [https://github.com/racket/racket/issues/1567](https://github.com/racket/racket/issues/1567) (may be tricky)
- [https://github.com/racket/racket/issues/1463](https://github.com/racket/racket/issues/1463) (most of the detective work has already been done)
- [https://github.com/racket/racket/issues/1431](https://github.com/racket/racket/issues/1431)
- [https://github.com/racket/racket/issues/1400](https://github.com/racket/racket/issues/1400)
- [https://github.com/racket/racket/issues/1342](https://github.com/racket/racket/issues/1342) (candidate solution exists, need to push it the rest of the way, and other potential directions)
- [https://github.com/racket/racket/issues/1295](https://github.com/racket/racket/issues/1295)
- [https://github.com/racket/racket/issues/1092](https://github.com/racket/racket/issues/1092)
- [https://github.com/racket/pict/issues/2](https://github.com/racket/pict/issues/2) (may be deep)
- [https://github.com/racket/pict/issues/29](https://github.com/racket/pict/issues/29)
- [https://github.com/racket/slideshow/issues/2](https://github.com/racket/slideshow/issues/2)
- [https://github.com/racket/db/issues/10](https://github.com/racket/db/issues/10) (move old-style logging to actual loggers, document topics, etc.)
- [https://github.com/racket/xrepl/issues/4](https://github.com/racket/xrepl/issues/4)
- [https://github.com/racket/lazy/issues/3](https://github.com/racket/lazy/issues/3) (some (most?) of the detective work appears to be done)
- [https://github.com/racket/games/issues/5](https://github.com/racket/games/issues/5)
- [https://github.com/racket/math/issues/9](https://github.com/racket/math/issues/9)
- [https://github.com/racket/math/issues/2](https://github.com/racket/math/issues/2) (for someone well-versed in numerical analysis)
- [https://github.com/racket/draw/issues/9](https://github.com/racket/draw/issues/9)
- [https://github.com/racket/draw/issues/8](https://github.com/racket/draw/issues/8)
- [https://github.com/racket/plot/issues/13](https://github.com/racket/plot/issues/13)
- [https://github.com/racket/plot/issues/7](https://github.com/racket/plot/issues/7)
- [https://github.com/racket/plot/issues/6](https://github.com/racket/plot/issues/6)
- [https://github.com/racket/rackunit/issues/71](https://github.com/racket/rackunit/issues/71) (probably requires decent macro-fu)
- [https://github.com/racket/gui/issues/32](https://github.com/racket/gui/issues/32)
- [https://github.com/racket/gui/issues/16](https://github.com/racket/gui/issues/16) (cross-platform gui toolkit work)
- [https://github.com/racket/htdp/issues/10](https://github.com/racket/htdp/issues/10) (small doc bug)
- [https://github.com/racket/htdp/issues/5](https://github.com/racket/htdp/issues/5)
- [https://github.com/racket/scribble/issues/131](https://github.com/racket/scribble/issues/131)
- [https://github.com/racket/scribble/issues/120](https://github.com/racket/scribble/issues/120) (front end work)
- [https://github.com/racket/scribble/issues/112](https://github.com/racket/scribble/issues/112) (front end work)
- [https://github.com/racket/scribble/issues/76](https://github.com/racket/scribble/issues/76)
- [https://github.com/racket/scribble/issues/47](https://github.com/racket/scribble/issues/47)
- [https://github.com/racket/scribble/issues/23](https://github.com/racket/scribble/issues/23)
- [https://github.com/racket/scribble/issues/19](https://github.com/racket/scribble/issues/19)
- [https://github.com/racket/drracket/issues/130](https://github.com/racket/drracket/issues/130) (a lot of the detective work has already been done)
- [https://github.com/racket/drracket/issues/99](https://github.com/racket/drracket/issues/99)
- [https://github.com/racket/typed-racket/issues/595](https://github.com/racket/typed-racket/issues/595)
- [https://github.com/racket/typed-racket/issues/517](https://github.com/racket/typed-racket/issues/517)
