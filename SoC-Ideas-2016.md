Welcome! If you are a **student** who is interested in working on a Google Summer of Code project for [Racket](http://www.racket-lang.org), you are in the right place. For general information about eligbility, please look [here](https://summerofcode.withgoogle.com/get-started/) on the GSoC homepage. The projects listed here are ideas that the community is excited about and would be willing to mentor for. Note that you are not restricted to these ideas. If you have your own project idea, we encourage you to discuss it on the Racket [mailing list](http://groups.google.com/forum/#!forum/racket-users/).

For more advice on applying for a project, see the [student manual](http://write.flossmanuals.net/gsocstudentguide/what-is-google-summer-of-code/) page. Make sure to use our [[application template|SoC Student Application]] when you apply. We encourage you to get involved on [IRC](https://racket-lang.org/irc-chat.html) (`#racket` on Freenode.net) or the mailing list prior to applying. Submitting patches to Racket or starting to write code on github is even better. A good place to start is to try one of the small projects on the [[Intro Projects]] page.

If you are a **potential mentor** and/or **community member**, please feel free to add your own project ideas here. Project ideas should be substantial enough to take about 12 weeks, but self-contained enough not to take longer. If you are interested in mentoring a project, please list yourself under the potential mentors of that idea. Don't hesitate to add ideas if you can't mentor yourself; just leave it blank. When you add an idea, please follow the template shown below.

For advice on mentoring, see the [GSoC mentoring manual](http://en.flossmanuals.net/GSoCMentoring/).

For an idea of what project ideas are like for other orgs, see the ideas for [Clojure](http://dev.clojure.org/display/community/Project+Ideas+2016), [Scala](http://scala-lang.org/gsoc/2016.html), or for [Haskell](https://ghc.haskell.org/trac/summer-of-code/wiki/SoC).

## Project ideas ##

Follow the template below:
### Project template name ###
* **Summary:** provide a one or two sentence summary of the project.
* **Expected results:** provide a few reasons why this project would be useful.
* **Requirements:** any required experience or knowledge.
* **Difficulty:** how hard is the project, beginner, intermediate, expert
* **Possible mentor:** each projects needs at least one possible mentor.
* **Other:** any other notes. Use this space to outline project details, if any.

---

### Data table/frame library ###
* **Summary:** Build a library that provides data tables, like R's [data frames](http://cran.r-project.org/doc/manuals/R-lang.html#Data-frame-objects)/[data tables](https://github.com/Rdatatable/data.table/wiki), Python's [pandas](http://pandas.pydata.org/pandas-docs/stable/index.html) library, or Julia's [DataFrames](http://dataframesjl.readthedocs.org/en/latest/).

    Racket comes with a full-featured [plotting](http://docs.racket-lang.org/plot/index.html) library
    but does not have a complementary data manipulation library. A data table package would
    start to fill in that gap. Beyond basic data tables, the project could also integrate
    data manipulation techniques like those used in pandas or R's [reshape](http://had.co.nz/reshape/) library.
    The library should support importing data from standard formats such as CSV.
    
* **Expected results:** A library for data tables that interoperates with [plot](http://docs.racket-lang.org/plot/index.html). It should support missing data, grouping, reshaping, and serialization/deserialization of data.
* **Requirements:** functional programming, numerical/stats/data programming, experience with R or similar languages a plus
* **Difficulty:** beginner or intermediate (depending on how sophisticated the feature set is)
* **Possible mentors:** Asumu Takikawa
* **Other:** This project would be a valuable contribution since it's one of the missing
    pieces that would help make Racket more useful for data analysis and science disciplines.
    It would be a good idea to solicit design ideas on the Racket mailing list since there are
    some scientific Racket users who might have feature requests.

---

### Improve DrRacket vim plugin ###
* **Summary:** A plugin for DrRacket that provides vim emulation
  (in the spirit of viper-mode or evil-mode) is under
  active development: https://github.com/takikawa/drracket-vim-tool.
  The plugin, however, lacks a lot of features that are needed to
  fully emulate vim. This project consists of improving the plugin
  to cover the most used keybindings and features of vim.
* **Expected results:** A more complete implementation of vim emulation.
  Example milestones might include specifying the vim commands using
  a DSL for ease-of-extension. Another one is fleshing out the Ex
  command parser to be more general.
* **Requirements:** object-oriented programming, GUI programming, knowledge of vi/vim
* **Difficulty:** beginner
* **Possible mentor:** Asumu Takikawa
* **Other:** This project is a relatively easy one that would be suitable for beginners
   because there is a substantial existing codebase. That means, however, that
   a candidate should be prepared to implement several distinct features in the GSoC
   work period.

   A good starting point for this project is to familiarize yourself with the
   Racket [GUI](http://docs.racket-lang.org/gui/index.html) library and the
   DrRacket [plugin API](http://docs.racket-lang.org/tools/index.html). And of course
   the actual plugin codebase.

---

### Command-line REPL debugger ###
* **Summary:** The Racket command-line REPL (read-eval-print-loop) does not
           come with its own debugger. DrRacket comes with a break+step
           GUI debugger, but it cannot be used from the command-line.
           This project involves building a new debugger that integrates
           with the REPL and possibly with [XREPL](http://docs.racket-lang.org/xrepl/index.html).

    This may also require adding support at the Racket VM level,
    depending on what features the debugger will have. One possible
    implementation strategy would be to use [errortrace](http://docs.racket-lang.org/errortrace/index.html),
    which the GUI debugger also uses. The [GUI debugger codebase](https://github.com/racket/drracket/tree/master/drracket/gui-debugger)
    is also a good starting point.
* **Expected result:** a fully working command-line debugger with break points,
                   stepping, and the ability to resume from exceptional control flow.
* **Requirements:** functional programming, possibly some C knowledge for adding
                debugging support at the VM level.
* **Difficulty:** intermediate
* **Possible mentor:** Asumu Takikawa, Leif Andersen
* **Other:** It would be helpful to look at related projects in Lisp-like languages
  - [Guile's debugger](https://www.gnu.org/software/guile/docs/docs-1.8/guile-ref/Interactive-Debugger.html#Interactive-Debugger)
  - [Chez Scheme debugger](http://www.scheme.com/csug7/debug.html)
  - [Gambit Scheme debugger](http://www.iro.umontreal.ca/~gambit/doc/gambit.html#Debugging)
  - [Larceny Scheme debugger](http://larceny.ccs.neu.edu/doc/user-manual.html#id2551369)
  - [SBCL debugger](http://sbcl.org/manual/index.html#Debugger)
  - [Bigloo debugger paper](http://www-sop.inria.fr/mimosa/fp/Bugloo/doc/cia03.pdf)

---

### Memory profiler for Racket ###
* **Summary:** This project is for building a [memory profiler](http://valgrind.org/docs/valgrind2007.pdf) for Racket programs.
    Racket comes with several profiling tools, including a
    [statistical runtime profiler](docs.racket-lang.org/profile/). However, it does not
    currently come with any tools for precisely profiling memory use.

    This project would likely involve changes to the Racket runtime system and
    garbage collector to help track allocations and deallocations in order to
    determine memory use. A simpler alternative would be to sample after garbage
    collections in order to just profile memory pressure.
* **Expected results:** a memory profiling tool that would inform the user what
parts of their program is allocating memory. It should be usable from the command-line
like `raco profile` or as a library call.
* **Requirements/Difficulty:** intermediate to expert depending on the approach
* **Possible mentor:** Vincent St-Amour
* **Other:**
  - See Guile's [gcprof](https://www.gnu.org/software/guile/manual/html_node/statprof.html) for inspiration
  - Also see Go's [profiling tools](http://blog.golang.org/profiling-go-programs) which includes memory profiling

---

### Git support for DrRacket ###
* **Summary:** The goal of this project is to build a DrRacket plugin that supports
    manipulating git repositories to allow a programmer to version control their Racket
    programs. There are two possible implementation strategies. One is to implement a
    a Racket library that allows interaction with git repositories, using either the FFI
    or through supporting the git object format.

    The other option is to call out to the git executable on the machine.
* **Expected results:** A DrRacket plugin that allows initializing, adding files, committing,
    and other basic git operations from the GUI.
* **Requirements:** familiarity with C (if binding to libgit), functional programming, GUI programming
* **Possible mentors:** Leif Andersen
* **Other:**
   - Some work on git bindings can be found [here](https://github.com/jarnaldich/racket-git).
   - Racket also comes with a library that supports git checkouts from remote servers. This
     can be re-used for this project by integrating it into the GUI.

---

### Game development support for Racket ###
* **Summary:** Racket has some old bindings for [SDL](https://github.com/cosmez/racket-sdl), as well as [pict3d](https://github.com/ntoronto/pict3d), a functional interface to rendering 3D pictures. However, Racket's support for creating video games could be improved. This could include anything from updating the SDL bindings to work with the latest versions for Racket and SDL, to creating bindings to [SFML](http://www.sfml-dev.org/), or even adding support for using game pad controllers to Racket. Proposals may include building their own game framework, however such projects must contain enough detail to explain how they will make the project complete-able within the time constraints. This will include what libraries they plan to use to reduce their workload.
* **Expected results:** Tools to help the creation of video games. This does not need to be an entire framework, but could be a port of one. The proposal must specify what the intent is.
* **Requirements:** Familiarity with game development. Functional programming experience a plus.
* **Difficulty:** Intermediate to Expert (Depending on scope of project)
* **Possible mentors:** Sam Caldwell, Leif Andersen
* **Other:**

---

### A graph layout library for Racket ###
* **Summary:** Graph layout is frequently needed for visualization
           and UI programming. The currently solution is to call
           out to graphviz, but applications could have more
           flexibility if a native Racket library or DSL that
           translates to graphviz were available.
           This project calls for designing such a library.
* **Expected result:** a graph layout library that can substitute [Graphviz](http://www.graphviz.org/) in Racket applications. It should be integrated with the existing [graph](https://github.com/stchang/graph) library for Racket.
* **Requirements:** functional programming, GUI programming
* **Difficulty:** beginner to intermediate
* **Possible mentors:** Stephen Chang
* **Other:**

---

### Pure Racket line editing for XREPL with paren-matching and other goodies ###
* **Summary:** Replace the `readline` library that ships with Racket with an implementation
    in pure Racket. Currently the library is implemented using an FFI binding to
    either libedit or to readline. Unfortunately, libedit does not provide some features
    that are available in readline and readline's license is incompatible with the one
    that Racket uses for its standard libraries.

    One starting point is to look at the [CharTerm](http://planet.racket-lang.org/display.ss?package=charterm.plt&owner=neil)
    library in the user-contributed package server.
* **Expected results:** A full-featured replacement of the `readline` library that
    is suitable for the Racket REPL's line editing.
* **Requirements:** functional programming, ideally experience with terminal UI programming
* **Difficulty:** intermediate
* **Possible mentor:** Leif Andersen
* **Other:** See [Haskeline](https://github.com/judah/haskeline) for a similar project for Haskell.

---

### Collaborative editing in DrRacket ###
* **Summary:** Build a DrRacket plug-in to enable real-time collaborative editing
           of a source file. Possibly with fine-grained logging.
           Two or more different programmers each edit the same file
           simultaneously, and edits one of them make show up immediately
           on the others' screens. An implementation might use
           [libinfinity](http://infinote.org/) that is part of the [Gobby](https://gobby.github.io/)
           project to implement text synchronization.
* **Expected result:** a DrRacket plugin that implements collaborative editing.
* **Requirements:** functional programming, GUI programming, networking, FFI
* **Difficulty:** intermediate
* **Possible mentor:** Andrew Cobb
* **Other:**

---

### Video editing DSL ###
* **Summary:** Create a Domain Specific Language for Editing videos in Racket. To make this project possible, we recommend using [FFmpeg](https://www.ffmpeg.org/) for the actual encoding. The [MLT](https://mltframework.org/) framework is another library that most video editing applications use. The goal of the DSL is to automate many of the repetitive tasks in editing videos. Adding support for DrRacket would be a stretch goal. This project will be implementation heavy, and thus require a lot of the design done ahead of time or very near the beginning of the project.

    The benefit of a DSL-based approach is that the effects and timeline for the video
    can be specified in text using version-control. And by using the usual abstractions like
    functions, a programmer could automate certain editing patterns. For example, the user
    could write a function that adds an intro or outro clip to a series of videos.
* **Expected result:** A DSL that can be used for rendering video. The DSL does not need to have many bells and whistles, but it does need to be complete enough to render video and do simple cuts.
* **Requirements:** Understanding of DSL design and implementation in the Racket ecosystem, understanding of video editing concepts.
* **Difficulty:** expert
* **Possible mentor:** Bryan Lachance, Asumu Takikawa, Leif Andersen
* **Other:**

---

### Racket GUI library for Android (DrRacket in Android) ###
* **Summary:** Currently minimal Racket can be [compiled for Android](http://www.wedesoft.de/racket-on-android.html), however, this lacks any support for running a Racket based GUI, and thus we cannot run DrRacket on Android. Creating a Racket based GUI library would be the first step to porting DrRacket to Android. This project will be hard to complete in the allotted time, and will require a motivated student who is already deeply familiar with Android, the Racket implementation, and GUI programming. Proposals will need to include both a scope of the GUI interface they would like to build, and mitigation plans if their proposal is too large.
* **Expected Results:** A Racket GUI running on Android capable that simple applications can use.
* **Benefits:** Brings GUIs to Racket programs on Android, first steps to running DrRacket on Android.
* **Requirements:** Experience with Racket GUI interface, GUI programming, and Android Platform.
* **Difficulty:** expert
* **Possible mentors:** Leif Andersen
* **Other:**

---

### Better Syntax Analysis for DrRacket ###
* **Summary:** DrRacket comes with a built-in online syntax analysis tool
  called "Check Syntax."
  This tool macro expands the user's program in the background
  and reports syntactic errors (e.g., a program with parse errors or
  with misuses of forms like `if` or `cond`) as they come up.
  This project aims to augment Check Syntax with more diagnostic information
  such as warning the user about unused definitions, missing `provide` declarations,
  or calling a function with the wrong number of arguments. This will require
  the use of some simple static analyses.
* **Expected results:** An expanded Check Syntax in DrRacket that will
  report more diagnostic information.
* **Requirements:** functional programming, GUI programming, knowledge of static analysis would help.
* **Difficulty:** beginner to intermediate, depending on how much analysis is done.
* **Possible mentors:** Spencer Florance
* **Other:** John Clement's [No-Brainer](http://planet.racket-lang.org/display.ss?package=no-brainer.plt&owner=clements) tool may be a good starting point.