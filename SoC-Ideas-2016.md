Welcome! If you are a **student** who is interested in working on a Google Summer of Code project for [Racket](http://www.racket-lang.org), you are in the right place. For general information about eligbility, please look [here](https://summerofcode.withgoogle.com/get-started/) on the GSoC homepage. The projects listed here are ideas that the community is excited about and would be willing to mentor for. Note that you are not restricted to these ideas. If you have your own project idea, we encourage you to discuss it on the Racket [mailing list](http://groups.google.com/forum/#!forum/racket-users/).

For more advice on applying for a project, see the [student manual](http://write.flossmanuals.net/gsocstudentguide/what-is-google-summer-of-code/) page. Make sure to use our [[application template|SoC Student Application]] when you apply. We encourage you to get involved on [IRC](https://racket-lang.org/irc-chat.html) (`#racket` on Freenode.net) or the mailing list prior to applying. Submitting patches to Racket or starting to write code on github is even better. A good place to start is to try one of the small projects on the [[Intro Projects]] page.

If you are a **potential mentor** and/or **community member**, please feel free to add your own project ideas here. Project ideas should be substantial enough to take about 12 weeks, but self-contained enough not to take longer. If you are interested in mentoring a project, please list yourself under the potential mentors of that idea. Don't hesitate to add ideas if you can't mentor yourself; just leave it blank. When you add an idea, please follow the template shown below.

For advice on mentoring, see the [GSoC mentoring manual](http://en.flossmanuals.net/GSoCMentoring/).

For an idea of what project ideas are like for other orgs, see the ideas for [GNOME](http://live.gnome.org/SummerOfCode2012/Ideas), [Scala](http://www.scala-lang.org/gsoc2011), or for [Haskell](http://hackage.haskell.org/trac/summer-of-code/report/1).

## Project ideas ##

Follow the template below:
### Project template name ###
* Summary: provide a one or two sentence summary of the project.
* Expected results: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Difficulty: how hard is the project, beginner, intermediate, expert
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

### Better Syntax Analysis for DrRacket ###
* Summary: DrRacket comes with a built-in online syntax analysis tool
  called "Check Syntax."
  This tool macro expands the user's program in the background
  and reports syntactic errors (e.g., a program with parse errors or
  with misuses of forms like `if` or `cond`) as they come up.
  This project aims to augment Check Syntax with more diagnostic information
  such as warning the user about unused definitions, missing `provide` declarations,
  or calling a function with the wrong number of arguments. This will require
  the use of some simple static analyses.
* Expected results: An expanded Check Syntax in DrRacket that will
  report more diagnostic information.
* Requirements: functional programming, GUI programming, knowledge of static analysis would help.
* Difficulty: beginner to intermediate, depending on how much analysis is done.
* Possible mentors: Robby Findler
* Other: John Clement's [No-Brainer](http://planet.racket-lang.org/display.ss?package=no-brainer.plt&owner=clements) tool may be a good starting point.

---

### Collaborative editing in DrRacket ###
* Summary: Build a DrRacket plug-in to enable real-time collaborative editing
           of a source file. Possibly with fine-grained logging.
           Two or more different programmers each edit the same file
           simultaneously, and edits one of them make show up immediately
           on the others' screens. An implementation might use
           [libinfinity](http://infinote.org/) that is part of the [Gobby](https://gobby.github.io/)
           project to implement text synchronization.
* Expected result: a DrRacket plugin that implements collaborative editing.
* Requirements: functional programming, GUI programming, networking, FFI
* Difficulty: intermediate
* Possible mentor: Robby Findler
* Other:

---

### A graph layout library for Racket ###
* Summary: Graph layout is frequently needed for visualization
           and UI programming. The currently solution is to call
           out to graphviz, but applications could have more
           flexibility if a native Racket library or DSL that
           translates to graphviz were available.
           This project calls for designing such a library.
* Expected result: a graph layout library that can substitute [Graphviz](http://www.graphviz.org/) in Racket applications. It should be integrated with the existing [graph](https://github.com/stchang/graph) library for Racket.
* Requirements: functional programming, GUI programming
* Difficulty: beginner to intermediate
* Possible mentors: Robby Findler
* Other:

---

### Universe programming for Android ###
* Summary: Build an Android client for Racket's [Universe](http://docs.racket-lang.org/teachpack/2htdpuniverse.html) protocol for interactive networked programs.
* Benefits: Brings Universe programming to a larger audience, brings Racket ideas to mobile devices.
* Requirements: Ideally experience with the Universe API and the Android platform.
* Possible mentors: David Van Horn
* Other:

---

### Data table/frame library ###
* Summary: Build a library that provides a data tables, like R's [data frames](http://cran.r-project.org/doc/manuals/R-lang.html#Data-frame-objects) or Python's [panda](http://pandas.pydata.org/pandas-docs/stable/index.html) library.
           Racket comes with a full-featured [plotting](http://docs.racket-lang.org/plot/index.html) library
           but does not have a complementary data manipulation library. A data table package would
           start to fill in that gap.
* Expected results: A library for data tables that interoperates with [plot](http://docs.racket-lang.org/plot/index.html).
* Requirements: functional programming, numerical/stats/data programming
* Difficulty: beginner
* Possible mentors: Asumu Takikawa
* Other:

---

### Git support for DrRacket ###
* Summary: Build a Racket library that allows interaction with git repositories.
* Benefits: Will make it easier to write scripts for development, Racket-based git tools in the future.
* Requirements: familiarity with C (if binding to libgit), functional programming and OO experience.
* Possible mentors:
* Other: Some work on git bindings can be found [here](https://github.com/jarnaldich/racket-git).

---


### Game development support for Racket ###
* Summary: Build libraries for game development on Racket. One possible first step is to build SDL bindings.
* Benefits: Fills a niche that people have requested for Racket development. Connects with the HtDP2e curriculum.
* Requirements: Familiarity with game development. Functional programming experience a plus.
* Possible mentors:
* Other:

---

### Memory profiler for Racket ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements/Difficulty: any required experience or knowledge. Difficulty if applicable.
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

### Video editing DSL ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Difficulty: how hard is the project, beginner, intermediate, expert
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

### Improve DrRacket vim plugin ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Difficulty: how hard is the project, beginner, intermediate, expert
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

### Command-line REPL debugger ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Difficulty: how hard is the project, beginner, intermediate, expert
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

### Pure Racket line editing for XREPL with paren-matching and other goodies ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Difficulty: how hard is the project, beginner, intermediate, expert
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

### RRB-Trees built into the Racket VM as an alternative to immutable vectors ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Difficulty: how hard is the project, beginner, intermediate, expert
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

Follow the template below:
### Project template name ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Difficulty: how hard is the project, beginner, intermediate, expert
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.
