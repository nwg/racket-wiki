# Larger Projects

For the more ambitious Racketeer ...

(Try [[Intro Projects]] if you are not ready for these)

* **a wiki written in Racket** to replace this [GitHub racket/racket wiki](https://github.com/racket/racket/wiki)
* Make a web page (demo.racket-lang ?) that contains Racket snippets. Use 
  the programs from http://rosettacode.org/wiki/Category:Racket to get started.
* **auto-completion of filenames in DrRacket**, probably using a pop-up. That is: I type a string containing a path fragment, and then I hit, say, C-c C-r or some other unused combination (ha!), and I get a dialog that will allow me with a small number of keystrokes to auto-complete to the filename that I’m looking for.
* Write **a parser for ispell dictionaries**. Make DrRacket use it.
* Write **a markdown parser** (important: lots of tests; support at least
  popular variants that are used by stackoverflow and github)
  - Available [here](https://github.com/greghendershott/markdown).
  - [Norman Gray](http://nxg.me.uk) has a WikiCreole parser [in the pkg collection](http://pkgs.racket-lang.org/#[squicky]) ([source](https://bitbucket.org/nxg/squicky)); a plan to extend this to Markdown was abandoned after Greg's package, above, ticked that box very thoroughly.

* Write a **gitolite replacement in Racket** (contact [Eli](mailto:eli@barzilay.org))
* `#lang scsh` -- or better: write just a library for similar bindings
  (macros & functions), and make it into a language that has shell-like
  syntax
* Write a **blogging framework**
  - write a **blog _web app_** - [Continue](https://docs.racket-lang.org/continue/index.html) is the beginning, needs user accounts (authentication & authorisation) added and [hosting](https://lexi-lambda.github.io/blog/2015/08/22/deploying-racket-applications-on-heroku/) options
  - ~Write a static web site generator (DONE) - [frog](https://github.com/greghendershott/frog/)~
* Write a **Common Lisp compatibility layer** (same functionality, but not
  all the core language features that would make this extremely
  difficult; for example: keep immutable pairs)
* Write a **Clojure compatibility layer**
  - Started on one [here](https://github.com/takikawa/racket-clojure) but it needs a lot more work.
* Write **bindings to SDL** (note that there are Allegro bindings on planet).
  - Work started [here](http://planet.racket-lang.org/display.ss?package=sdl4racket.plt&owner=pb82)
* Integrate the existing parser-tools [SRE](http://www.ccs.neu.edu/home/shivers/papers/sre.txt) with Racket regexps.
* Write some **code metrics tools** (number of functions, number of lines, etc) and integrate them with DrRacket's module browser.
* Write **image filters** [example](http://reference.wolfram.com/mathematica/guide/ImageFilteringAndNeighborhoodProcessing.html)

# Completed Projects

* Write a blogging framework
  - Static web site generator [frog](https://github.com/greghendershott/frog/).
* Write a YAML parser
  - Now available [on PLaneT](http://planet.racket-lang.org/display.ss?package=yaml.plt&owner=esilkensen).