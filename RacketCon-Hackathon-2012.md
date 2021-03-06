This is the organization page for the Hackathon at [RacketCon 2012](http://con.racket-lang.org/).

* Where: WVH 110
* When:  14 October, 10:00AM
* What to bring: a laptop

Food: we will be providing lunch (pizza)

The plan for the Hackathon is to encourage work on small, self-contained improvements that can be finished in a short amount of time. Of course, people are free to work on other projects if they would prefer. Racket developers will be around to give advice and help.

Some suggested projects are listed below. The main categories are documentation improvements, FFI bindings, and web APIs.

To make documentation improvements, fork the [Racket git repo](https://github.com/plt/racket) and make your changes there. Most of the core documentation can be found at `collects/scribblings/`. When you're done, submit a pull request and a developer will review and suggest changes or merge it. For help with pull requests, see the [GitHub help page](https://help.github.com/articles/using-pull-requests).

For other projects, PLaneT is probably the appropriate distribution channel. For help with making a PLaneT package, see [this page](http://pre.racket-lang.org/docs/html/planet/Developing_Packages_for_PLaneT.html) or ask around. Neil Van Dyke's [McFly](http://planet.racket-lang.org/package-source/neil/mcfly-tools.plt/1/10/planet-docs/doc/index.html) tool is also helpful.

***

**If you claim a project, mark it on the wiki.**

# Documentation improvements

See the Scribble [getting started](http://docs.racket-lang.org/scribble/getting-started.html) page for how to write documentation and also the Reference [style guide](http://docs.racket-lang.org/scribble/reference-style.html).

* Add code examples to Reference sections that lack or have few examples. Our goal is to have examples for all Reference entries. Some places to look: [string ports](http://pre.racket-lang.org/docs/html/reference/stringport.html), [reading](http://pre.racket-lang.org/docs/html/reference/Reading.html), [delayed evaluation](http://pre.racket-lang.org/docs/html/reference/Delayed_Evaluation.html), and so on. (Kevin & Michael & Xiangqi)

* Expand short Guide sections. Some sections are too short to explain difficult features, such as [continuations and control](http://pre.racket-lang.org/docs/html/guide/control.html).

* Create more tutorials. Some suggested topics:
  - Writing a GUI application
  - How to write & understand macros (Ryan & Claire)
  - Tutorial on classes, OO (Matthias & Danny)
	DONE http://www.ccs.neu.edu/home/matthias/Thoughts/Programming_with_Class_in_Racket.html 
  - Development how-to. (using raco, setting up your environment, writing tests, etc.)
  - How to get the most out of Racket tools (e.g., debugger, macro stepper) with screenshots
  - Extended FFI tutorial (Chris, after getting Java FFI working)

* Add a detailed example to the profiler manual.

# FFI Bindings

* [Google Snappy](http://code.google.com/p/snappy/) (Asumu & Stephen)
* Comprehensive [GStreamer](http://gstreamer.freedesktop.org/documentation/) bindings (Asumu has a small part of it [here](https://github.com/takikawa/racket-gst))
* [MurmurHash3](http://code.google.com/p/smhasher/) (either FFI binding or pure Racket reimplementation)
* [AudioFile](http://audiofile.68k.org/) (read and write audio files)
* [Sundown](https://github.com/vmg/sundown) (Markdown parser)
* [libnotify](http://developer.gnome.org/libnotify/) (GUI notifications)
* [gnome-keyring](http://developer.gnome.org/gnome-keyring/stable/)
* [bcrypt](http://www.openwall.com/crypt/)
* [OpenCV](http://opencv.org/)
* [libxslt](http://xmlsoft.org/XSLT/)
* [libaosd](https://github.com/atheme/libaosd) (on screen display)
* [LAPACK](http://www.netlib.org/lapack/) (BSD Licensed Matrix Library - in wide use for scientific computations)

# Web APIs

* [WeatherUnderground API](http://www.wunderground.com/weather/api/). [Other](http://blog.programmableweb.com/2009/04/15/5-weather-apis-from-weatherbug-to-weather-channel/) weather APIs.
* Write bindings to the Twitter APIs
* Write bindings to the Facebook APIs
* [Google Places](https://developers.google.com/places/documentation/) API
* [Google Prediction](https://developers.google.com/prediction/docs/getting-started) API
* [Google API Discovery](https://developers.google.com/discovery/) (Greg & Eli)

# Misc

* Write a version of the [shootout](http://shootout.alioth.debian.org/) [fannkuch-redux benchmark](http://shootout.alioth.debian.org/u32/performance.php?test=fannkuchredux).  Currently the only missing Racket program. (Danny Yoo is working on this)
* A harder project for someone with JS and maybe Racket webserver chops: something like [tryclj.com](http://tryclj.com/) for Racket that looks nice and possibly comes with a tutorial. Useful things to know: [jquery-console](https://github.com/chrisdone/jquery-console), the Racket [sandbox](http://docs.racket-lang.org/reference/Sandboxed_Evaluation.html).
* Hack on TR (Neil & Vincent)

# Results

Add links here to commits, repositories, pull requests, web pages, or anything else that's a result of the Hackathon.

* Explanations of short Racket examples: https://github.com/samth/racket-examples
* https://github.com/plt/racket/pull/150
* https://github.com/plt/racket/pull/151
* https://github.com/plt/racket/pull/152
* https://github.com/plt/racket/pull/153
* https://github.com/plt/racket/pull/154
* Commits: https://github.com/plt/racket/compare/93784be7...5bc108c7
* https://github.com/plt/racket/commit/2c56ace436
* https://github.com/plt/racket/commit/79ada3b16e
* Snappy: https://github.com/stchang/snappy (http://planet.racket-lang.org/display.ss?package=snappy.plt&owner=plt)
* MurmurHash3: https://github.com/jrslepak/murmur3
* Rackona: https://github.com/cky/rackona
* Google API Discovery (40+ Google web services): On [GitHub](https://github.com/greghendershott/gapi) and [PLaneT](http://planet.racket-lang.org/display.ss?package=gapi.plt&owner=gh)
* DrRacket string constant spell checker: https://github.com/plt/racket/compare/5bc108c7...a59df8c7
https://github.com/plt/racket/commit/4787361d
* Macro Tutorial: https://github.com/rmculpepper/malr/
