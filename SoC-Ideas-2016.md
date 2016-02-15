Welcome! If you are a **student** who is interested in working on a Google Summer of Code project for [Racket](http://www.racket-lang.org), you are in the right place. For general information about eligbility, please look [here](https://summerofcode.withgoogle.com/get-started/) on the GSoC homepage. The projects listed here are ideas that the community is excited about and would be willing to mentor for. Note that you are not restricted to these ideas. If you have your own project idea, we encourage you to discuss it on the Racket [mailing list](http://groups.google.com/forum/#!forum/racket-users/).

For more advice on applying for a project, see the [student manual](http://write.flossmanuals.net/gsocstudentguide/what-is-google-summer-of-code/) page. Make sure to use our [[application template|SoC Student Application]] when you apply. We encourage you to get involved on [IRC](https://racket-lang.org/irc-chat.html) (`#racket` on Freenode.net) or the mailing list prior to applying. Submitting patches to Racket or starting to write code on github is even better. A good place to start is to try one of the small projects on the [[Intro Projects]] page.

If you are a **potential mentor** and/or **community member**, please feel free to add your own project ideas here. Project ideas should be substantial enough to take about 12 weeks, but self-contained enough not to take longer. If you are interested in mentoring a project, please list yourself under the potential mentors of that idea. Don't hesitate to add ideas if you can't mentor yourself; just leave it blank. When you add an idea, please follow the template shown below.

For advice on mentoring, see the [GSoC mentoring manual](http://en.flossmanuals.net/GSoCMentoring/).

For an idea of what project ideas are like for other orgs, see the ideas for [GNOME](http://live.gnome.org/SummerOfCode2012/Ideas), [Scala](http://www.scala-lang.org/gsoc2011), or for [Haskell](http://hackage.haskell.org/trac/summer-of-code/report/1).

## Project ideas ##

Follow the template below:
### Project template name ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Difficulty: how hard is the project, beginner, intermediate, expert
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

### Extend Check Syntax ###
* Summary: DrRacket has a great built-in online syntax analysis tool. However, it would be even better if it reported more diagnostic information such as unused definitions, unprovided definitions, and some easy static analysis (e.g., arity analysis).
* Benefits: Makes developers lives easier. Might help students as well.
* Requirements: Functional programming, GUI programming experience is good. Also experience with programs that process other programs.
* Possible mentors: Robby Findler
* Other: John Clement's [No-Brainer](http://planet.racket-lang.org/display.ss?package=no-brainer.plt&owner=clements) tool may be a good starting point.

---

### DrRacket tool for collaborative editing ###
* Summary: a DrRacket plug-in to enable real-time collaborative editing of a source file, possibly with fine-grained logging as well.  Two or more different programmers each edit the same file simultaneously, and edits one of them make show up immediately on the others' screens.
* Benefits: Collaborative editing has various benefits to students and developers. The logging functionality could allow an instructor to pinpoint mistakes a student makes.
* Requirements/Difficulty: Functional programming experience and GUI programming experience. Ideally some experience with networking.
* Possible mentor: Robby Findler
* Other:

### Design a graph layout library for Racket ###
* Summary: DrRacket makes use of graph layout algorithms frequently in many parts of the UI. This project would involve writing a native Racket library that can handle that.
* Benefits: Would allow more graph-based UIs in DrRacket and other Racket programs.
* Requirements: Experience with functional programming and GUI programming.
* Possible mentors: Robby Findler
* Other: Functionality similar to [Graphviz](http://www.graphviz.org/) is desirable. One mode of operation might be to call out to Graphviz via the FFI.

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
* Benefits: Fills a gap for Racket in statistical computing. Could tie into other tools like the `plot` library.
* Requirements: Familiarity with numerical/statistical computing (R, Numpy, or other). Functional programming experience.
* Possible mentors:
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
