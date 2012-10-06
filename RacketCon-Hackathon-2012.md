This is the organization page for the Hackathon at [RacketCon 2012](http://con.racket-lang.org/).

* Where: WVH 110
* When:  14 October (precise time TBA)

The plan for the Hackathon is to encourage work on small, self-contained improvements that can be finished in a short amount of time. Of course, people are free to work on other projects if they would prefer. Racket developers will be around to give advice and help.

Some suggested projects are listed below. The main categories are documentation improvements, FFI bindings, and web APIs.

To make documentation improvements, fork the Racket git repo and make your changes there. Most of the core documentation can be found at `collects/scribblings/`. When you're done, submit a pull request and a developer will review and suggest changes or merge it. For help with pull requests, see the [GitHub help page](https://help.github.com/articles/using-pull-requests).

For other projects, PLaneT is probably the appropriate distribution channel. For help with making a PLaneT package, see [this page](http://pre.racket-lang.org/docs/html/planet/Developing_Packages_for_PLaneT.html) or ask around. Neil Van Dyke's [McFly](http://planet.racket-lang.org/package-source/neil/mcfly-tools.plt/1/10/planet-docs/doc/index.html) tool is also helpful.

***

# Documentation improvements

* Add code examples to Reference sections that lack or have few examples. Examples: [string ports](http://pre.racket-lang.org/docs/html/reference/stringport.html), [reading](http://pre.racket-lang.org/docs/html/reference/Reading.html), [delayed evaluation](http://pre.racket-lang.org/docs/html/reference/Delayed_Evaluation.html), and so on.

* Expand short Guide sections. Some sections are too short to explain difficult features, such as [continuations and control](http://pre.racket-lang.org/docs/html/guide/control.html).

* Create more tutorials. Some suggested topics:
  - Writing a GUI application
  - How to write & understand macros
  - Tutorial on classes, OO
  - Development how-to. (using raco, setting up your environment, writing tests, etc.)
  - How to get the most out of Racket tools (e.g., debugger, macro stepper) with screenshots
  - Extended FFI tutorial

* Add a detailed example to the profiler manual.

# FFI Bindings

# Web APIs

* Write bindings to the Twitter APIs
* Write bindings to the Facebook APIs

# Misc

* Write a version of the [shootout](http://shootout.alioth.debian.org/) [fannkuch-redex benchmark](http://shootout.alioth.debian.org/u32/performance.php?test=fannkuchredux).  Currently the only missing Racket program.