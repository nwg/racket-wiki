Welcome! If you are a **student** who is interested in working on a Google Summer of Code project for [Racket](http://www.racket-lang.org), you are in the right place. For general information about eligbility, please look [here](http://socghop.appspot.com/document/show/gsoc_program/google/gsoc2012/faqs#student_eligibility) on Google's FAQ. The projects listed here are ideas that the community is excited about and would be willing to mentor for. Note that you are not restricted to these ideas. If you have your own project idea, we encourage you to discuss it on the Racket [mailing list](http://lists.racket-lang.org/users/).

For more advice on applying for a project, see Google's [advice for students](http://code.google.com/p/google-summer-of-code/wiki/AdviceforStudents) page. Make sure to use our [[application template|SoC Student Application]] when you apply. We encourage you to get involved on [IRC](http://www.racket-lang.org/community.html) (`#racket` on Freenode.net) or the mailing list prior to applying. Submitting patches to Racket or starting to write code on github is even better. A good place to start is to try one of the small projects on the [[Intro Projects]] page.

If you are a **potential mentor** and/or **community member**, please feel free to add your own project ideas here. Project ideas should be substantial enough to take about 12 weeks, but self-contained enough not to take longer. If you are interested in mentoring a project, please list yourself under the potential mentors of that idea. Don't hesitate to add ideas if you can't mentor yourself; just leave it blank. When you add an idea, please follow the template shown below.

For advice on mentoring, see the [GSoC mentoring manual](http://en.flossmanuals.net/GSoCMentoring/).

For an idea of what project ideas are like for other orgs, see the ideas for [GNOME](http://live.gnome.org/SummerOfCode2012/Ideas), [Scala](http://www.scala-lang.org/gsoc2011), or for [Haskell](http://hackage.haskell.org/trac/summer-of-code/report/1).

## Project ideas ##

Follow the template below:
### Project template name ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements/Difficulty: any required experience or knowledge. Difficulty if applicable.
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

---

### DrRacket tool for collaborative editing ###
* Summary: a DrRacket plug-in to enable real-time collaborative editing of a source file, possibly with fine-grained logging as well.  Two or more different programmers each edit the same file simultaneously, and edits one of them make show up immediately on the others' screens.
* Benefits: Collaborative editing has various benefits to students and developers. The logging functionality could allow an instructor to pinpoint mistakes a student makes.
* Requirements/Difficulty: Functional programming experience and GUI programming experience. Ideally some experience with networking.
* Possible mentor: Robby Findler
* Other:

---

### Compiler from Redex patterns to `racket/match` ###
* Summary: [Redex](http://docs.racket-lang.org/redex/index.html) is a domain-specific language for designing programming language semantics. This project entails building a compiler from Redex's pattern language (used to describe terms and expressions) to the pattern language used by `racket/match`.
* Benefits: More efficient pattern matching for Redex, which is used by the core dev team and other community members.
* Requirements: Experience with functional programming, especially pattern matching. Ideally some experience with PL semantics.
* Possible mentors: Robby Findler
* Other: For more information about Redex, look at the [reference manual](http://docs.racket-lang.org/redex/index.html) and the [Semantics Engineering with PLT Redex](http://redex.racket-lang.org/) website.

---

### Extend Check Syntax ###
* Summary: DrRacket has a great built-in online syntax analysis tool. However, it would be even better if it reported more diagnostic information such as unused definitions, unprovided definitions, and some easy static analysis (e.g., arity analysis).
* Benefits: Makes developers lives easier. Might help students as well.
* Requirements: Functional programming, GUI programming experience is good. Also experience with programs that process other programs.
* Possible mentors: Robby Findler
* Other: John Clement's [No-Brainer](http://planet.racket-lang.org/display.ss?package=no-brainer.plt&owner=clements) tool may be a good starting point.

---

### Implement proper indentation for Scribble documents ###
* Summary: Scribble is a language-based documentation format for Racket. Scribble documents are currently not indented properly in DrRacket. This project involves implementing proper tabbing for Scribble and extending DrRacket to allow language-specific tabbing.
* Benefits: Scribble would be easier to use for developers. Language-specific indentation could be useful in the future for different languages.
* Requirements: Functional programming experience.
* Possible mentors: Robby Findler
* Other:

---

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

### Write a git hosting system for Racket ###
* Summary: Build a git hosting system (like gitolite, but with more features) for managing Racket repositories.
* Benefits: Reduces dependency of Racket development on software in other languages.
* Requirements/Difficulty: Knowledge of gitolite or similar systems. Functional programming experience. This is a more ambitious project.
* Possible mentors: Eli Barzilay
* Other:

---

### Racket shell support ###
* Summary: Design and implement a Racket shell language that supports processes, regular expressions, and other tools needed for shell scripting.
* Benefits: Another niche for Racket dogfooding. Fills a scripting role Racket is not currently ideal for.
* Requirements: Familiarity with shell scripting. Functional programming experience.
* Possible mentors: Eli Barzilay
* Other: See [scsh](http://www.scsh.net/) for inspiration. The goal is not full compatibility with scsh, but the ideas may be importable.

---

### Scripting language for Google SketchUp ###
* Summary: Allow Racket to be used as scripting language for Google SketchUp.
* Benefits: Designers and architects that employ generative design techniques. Very useful in education.
* Requirements: Familiarity with (some) CAD application and Racket.
* Possible mentors: Antonio Menezes Leitao
* Other:

---

### SIMD Intrinsics ###
* Summary: Provide access to SIMD operations for fast numeric computing.
* Benefits: Fast numeric computation is necessary for computer audio and vision, and scientific computing.
* Requirements/Difficulty: all CS undergrads should have the basic knowledge required.
* Possible mentor: can I nominate Matthew Flatt?.
* Other: The notes on adding SIMD to Haskell might be useful: http://hackage.haskell.org/trac/ghc/wiki/SIMD

The basic implementation would provide SIMD intrinsics that operate on fl/fxvector similar to the existing fx/fl operations. Better implementations would build abstractions on top of these leading to further speedup and ease-of-use. It might require hacking the JIT or alternatively by building a little language for expressing SIMD operations along with a custom compiler.

---

### An Assembler ###
* Summary: build an in-memory assembler in Racket.
* Benefits: Racket is the premier language for language exploration, but it doesn't support experimentation with runtime characteristics. This requires custom code generation. Complex projects might want something like LLVM but for just messing around an assembler is a good way to get started. It also allows exploration of systems programming (you can call into the kernel directly). 
* Requirements/Difficulty: a willingness to get stuck into low-level detail.
* Possible mentor: Noel Welsh.
* Other: there are some existing projects:

https://github.com/noelwelsh/assembler

https://github.com/darius/miasma

---

### Data table/frame library ###
* Summary: Build a library that provides a data tables, like R's [data frames](http://cran.r-project.org/doc/manuals/R-lang.html#Data-frame-objects) or Python's [panda](http://pandas.pydata.org/pandas-docs/stable/index.html) library.
* Benefits: Fills a gap for Racket in statistical computing. Could tie into other tools like the `plot` library.
* Requirements: Familiarity with numerical/statistical computing (R, Numpy, or other). Functional programming experience.
* Possible mentors:
* Other:
 
---

### Bindings to OpenCV ###
* Summary: Bindings to OpenCV, the cross-platform image-capture and machine-vision toolkit.
* Benefits: Lets Racket capture and process video streams and still images from webcams etc. Lets Racket perform machine vision tasks. Provides ingredients for making engaging teaching projects.
* Requirements/Difficulty: FFI bindings. Needs access to a webcam. Possibly experience with integrating libraries into the Racket build system - it'd be nice to have it available easily for students on all platforms, but that's just a nice-to-have.
* Possible mentor:
* Other: 

---

### Git library for Racket ###
* Summary: Build a Racket library that allows interaction with git repositories.
* Benefits: Will make it easier to write scripts for development, Racket-based git tools in the future.
* Requirements: familiarity with C (if binding to libgit), functional programming and OO experience.
* Possible mentors:
* Other: Some work on git bindings can be found [here](https://github.com/jarnaldich/racket-git).

---

### Write libraries to interact with Wii Remotes and/or game controllers ###
* Summary: Write a library for interacting with Wiimotes for Racket.
* Benefits: A library niched that isn't filled yet. Potentially useful in education.
* Requirements: Familiarity with functional programming and ideally with foreign-function interface bindings.
* Potential mentors:
* Other: 
  - If the Wiimote library is just building an FFI binding, it may not take the whole 12 weeks,
    so this project should also try to support other kinds of controllers. Building a generic
    functional abstraction for game controllers would be an interesting challenge.
  - [Technical details](http://wiibrew.org/wiki/Wiimote) on the Wiimote
  - [wiiuse](http://sourceforge.net/projects/wiiuse/) has code for the Wiimote's protocol, as well as Win/Linux bluetooth code
  - Mac OSX [Bluetooth Dev info](http://developer.apple.com/library/mac/#documentation/DeviceDrivers/Conceptual/Bluetooth/BT_Intro/BT_Intro.html)
  - A game controller interface exists for [Mac OS X](https://github.com/get-bonus/get-bonus/blob/master/exp/joystick.rkt), but an interface should be normalized and available across platforms.
  - Maybe use [libsdl](http://www.libsdl.org/)?

---

### Game development support for Racket/Bindings to SDL. ###
* Summary: Build libraries for game development on Racket. One possible first step is to build SDL bindings.
* Benefits: Fills a niche that people have requested for Racket development. Connects with the HtDP2e curriculum.
* Requirements: Familiarity with game development. Functional programming experience a plus.
* Possible mentors:
* Other:
