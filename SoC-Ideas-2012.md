Welcome! If you are a student who is interested in working on a Google Summer of Code project for [Racket](http://www.racket-lang.org), you are in the right place. For general information about eligbility, please look [here](http://socghop.appspot.com/document/show/gsoc_program/google/gsoc2012/faqs#student_eligibility) on Google's FAQ. The projects listed here are ideas that the community is excited about and would be willing to mentor for. Note that you are not restricted to these ideas. If you have your own project idea, we encourage you to discuss it on the Racket [mailing list](http://lists.racket-lang.org/users/).

If you are a potential mentor and community member, please feel free to add your own project ideas here. Project ideas should be substantial enough to take about 12 weeks, but self-contained enough not to take longer. If you are interested in mentoring a project, please list yourself under the potential mentors of that idea. When you add an idea, please follow the template shown below.

## Project ideas ##

Follow the template below:
### Project template name ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

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

### Write a gitolite replacement in Racket (contact [Eli](mailto:eli@barzilay.org)) ###
* Summary:
* Benefits:
* Requirements:
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

### Write bindings to SDL. In general, game dev. support for Racket ###
* Summary: Build libraries for game development on Racket. One possible first step is to build SDL bindings.
* Benefits:
* Requirements:
* Possible mentors:
* Other:

---