These are project ideas for the Google Summer of Code 2012 for the Racket programming language.

If you add another project idea, please follow the format:
### Project name ###
* Summary: provide a one or two sentence summary of the project.
* Benefits: provide a few reasons why this project would be useful.
* Requirements: any required experience or knowledge.
* Possible mentor: each projects needs at least one possible mentor.
* Other: any other notes. Use this space to outline project details, if any.

### Github integration for Racket ###
* Summary: Implement github code highlighting, code editing, and other features to allow better Racket integration on github.
* Benefits: Allows the Racket community to take more advantage of github.
* Requirements: Functional programming experience. Knows about git/github. Ideally some familiarity with the internals of github.
* Possible mentor:

### DrRacket support for git ###
* Summary: Build a DrRacket plugin/tool that allows integration with git.
* Benefits: Better support for core developers, brings DrRacket closer to other IDEs, possibly teaching benefits.
* Requirements: familiarity with C (for FFI binding to libgit), functional programming and OO experience. Ideally experience with GUI programming.
* Possible mentors: Asumu Takikawa
* Other: Some work on git bindings can be found [here](https://github.com/jarnaldich/racket-git).

### Write libraries to interact with Wii Remotes ###
  - [Technical details](http://wiibrew.org/wiki/Wiimote) on the Wiimote
  - [wiiuse](http://sourceforge.net/projects/wiiuse/) has code for the Wiimote's protocol, as well as Win/Linux bluetooth code
  - Mac OSX [Bluetooth Dev info](http://developer.apple.com/library/mac/#documentation/DeviceDrivers/Conceptual/Bluetooth/BT_Intro/BT_Intro.html)
* Write libraries to interact with game controllers
  - This exists on for [Mac OS X](https://github.com/get-bonus/get-bonus/blob/master/exp/joystick.rkt), but an interface should be normalized and available across platforms.
  - maybe use [libsdl](http://www.libsdl.org/)?

### Write a gitolite replacement in Racket (contact [Eli](mailto:eli@barzilay.org)) ###
* Summary:
* Benefits:
* Requirements:
* Possible mentors:
* Other:

### `#lang scsh` or Racket shell support ###
* Summary: Design and implement a Racket shell language that supports processes, regular expressions, and other tools needed for shell scripting.
* Benefits: Another niche for Racket dogfooding. Fills a scripting role that currently Racket is not ideal for.
* Requirements: Some familiarity with shell scripting. Functional programming experience.
* Possible mentors:
* Other:

### Write bindings to SDL. In general, game dev. support for Racket ###
* Summary: Build libraries for game development on Racket. One possible first step is to build SDL bindings.
* Benefits:
* Requirements:
* Possible mentors:
* Other:
* Other:
