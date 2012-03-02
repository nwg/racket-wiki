Welcome! If you are a **student** who is interested in working on a Google Summer of Code project for [Racket](http://www.racket-lang.org), you are in the right place. For general information about eligbility, please look [here](http://socghop.appspot.com/document/show/gsoc_program/google/gsoc2012/faqs#student_eligibility) on Google's FAQ. The projects listed here are ideas that the community is excited about and would be willing to mentor for. Note that you are not restricted to these ideas. If you have your own project idea, we encourage you to discuss it on the Racket [mailing list](http://lists.racket-lang.org/users/).

For more advice on applying for a project, see Google's [advice for students](http://code.google.com/p/google-summer-of-code/wiki/AdviceforStudents) page. We encourage you to get involved on [IRC](http://www.racket-lang.org/community.html) or the mailing list prior to applying. Submitting patches to Racket or starting to write code on github is even better.

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

### Bindings to OpenCV ###
* Summary: Bindings to OpenCV, the cross-platform image-capture and machine-vision toolkit.
* Benefits: Lets Racket capture and process video streams and still images from webcams etc. Lets Racket perform machine vision tasks. Provides ingredients for making engaging teaching projects.
* Requirements/Difficulty: FFI bindings. Needs access to a webcam. Possibly experience with integrating libraries into the Racket build system - it'd be nice to have it available easily for students on all platforms, but that's just a nice-to-have.
* Possible mentor:
* Other: 

---

### DrRacket support for git ###
* Summary: Build a DrRacket plugin/tool that allows integration with git.
* Benefits: Better support for core developers, brings DrRacket closer to other IDEs, possibly teaching benefits.
* Requirements: familiarity with C (for FFI binding to libgit), functional programming and OO experience. Ideally experience with GUI programming.
* Possible mentors: Asumu Takikawa
* Other: Some work on git bindings can be found [here](https://github.com/jarnaldich/racket-git).

---

### Universe programming for Android ###
* Summary: Build an Android client for Racket's [Universe](http://docs.racket-lang.org/teachpack/2htdpuniverse.html) protocol for interactive networked programs.
* Benefits: Brings Universe programming to a larger audience, brings Racket ideas to mobile devices.
* Requirements: Ideally experience with the Universe API and the Android platform.
* Possible mentors: David Van Horn
* Other:

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

### Write a gitolite replacement in Racket ###
* Summary: Build a replace for gitolite, which is software that manages the internal development repositories for Racket.
* Benefits: Reduces dependency of Racket development on software in other languages.
* Requirements/Difficulty: Knowledge of gitolite or similar systems. Functional programming experience. This is a more ambitious project.
* Possible mentors:
* Other:

---

### `#lang scsh` or Racket shell support ###
* Summary: Design and implement a Racket shell language that supports processes, regular expressions, and other tools needed for shell scripting.
* Benefits: Another niche for Racket dogfooding. Fills a scripting role that currently Racket is not ideal for.
* Requirements: Some familiarity with shell scripting. Functional programming experience.
* Possible mentors:
* Other:

---

### Game development support for Racket/Bindings to SDL. ###
* Summary: Build libraries for game development on Racket. One possible first step is to build SDL bindings.
* Benefits: Fills a niche that people have requested for Racket development. Connects with the HtDP2e curriculum.
* Requirements: Familiarity with game development. Functional programming experience a plus.
* Possible mentors:
* Other:

---