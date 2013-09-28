This is the organization page for the Hackathon at [RacketCon 2013](http://con.racket-lang.org/).

* Where: West Village H Room 108
* When:  28 September, 2013 10AM-5PM
* What to bring: a laptop

Food: we will be providing lunch (pizza)

The plan for the Hackathon is to encourage work on small, self-contained improvements that can be finished in a short amount of time. Of course, people are free to work on other projects if they would prefer. Racket developers will be around to give advice and help.

Some suggested projects are listed below. We encourage anyone writing libraries to upload them to the package server (see the docs on the [package system](http://www.cs.utah.edu/plt/snapshots/current/doc/pkg/index.html)).

To make documentation improvements, fork the [Racket git repo](https://github.com/plt/racket) and make your changes there. Most of the core documentation can be found at `collects/scribblings/`. When you're done, submit a pull request and a developer will review and suggest changes or merge it. For help with pull requests, see the [GitHub help page](https://help.github.com/articles/using-pull-requests).

Also see the [2012 page](https://github.com/plt/racket/wiki/RacketCon-Hackathon-2012) and the [Intro Projects](https://github.com/plt/racket/wiki/Intro-Projects) page.

***

**If you claim a project, mark it on the wiki.**

# Documentation Improvements

* Tutorials. More tutorials or even sections of tutorials would be helpful. This is a project where multiple people can work together easily, possibly by splitting the work by section (and having someone do an editing pass to make it cohesive). Potential tutorial topics:
  - `racket/gui` (e.g., [Qt Quick](http://qt-project.org/doc/qt-5.1/qtdoc/gettingstartedqml.html), [GTK getting started](https://developer.gnome.org/gtk3/stable/gtk-getting-started.html))
  - `racket/draw`
  - Concurrency and synchronization (e.g., see [Rust tasks tutorial](http://static.rust-lang.org/doc/tutorial-tasks.html) or [Qt Threads](http://qt-project.org/doc/qt-5.1/qtcore/thread-basics.html) for inspiration)
  - File I/O, command-line applications

# FFI Bindings

# More involved projects

* Add additional GUI widgets.
  - For example, a progress indicator/spinner. It has support on [Cocoa](https://developer.apple.com/library/mac/#documentation/Cocoa/Reference/ApplicationKit/Classes/nsprogressindicator_Class/Reference/Reference.html), [Win32](http://msdn.microsoft.com/en-us/library/windows/desktop/bb760816%28v=vs.85%29.aspx) (see marquee mode), and [GTK](https://developer.gnome.org/gtk3/stable/GtkSpinner.html)
  - Tooltips. [Win32](http://msdn.microsoft.com/en-us/library/windows/desktop/bb760250%28v=vs.85%29.aspx), [Cocoa](https://developer.apple.com/library/mac/#documentation/Cocoa/Reference/ApplicationKit/Classes/NSView_Class/Reference/NSView.html) (see `setToolTip`), [GTK](https://developer.gnome.org/gtk3/3.7/GtkTooltip.html). Note that DrRacket has a class that supports tooltips, but implemented in Racket and not natively. The use in DrRacket might be a good test.
  - Spin button/stepper/up-down button. [Cocoa](https://developer.apple.com/library/mac/#documentation/cocoa/reference/ApplicationKit/Classes/NSStepper_Class/Reference/Reference.html), [GTK](https://developer.gnome.org/gtk3/stable/GtkSpinButton.html), [Win32](http://msdn.microsoft.com/en-us/library/windows/desktop/bb759889%28v=vs.85%29.aspx)

* Implement a library for [HAMT](http://en.wikipedia.org/wiki/Hash_array_mapped_trie)s.

# Pick something from "rudybot"s TODO list

[rudybot](https://github.com/offby1/rudybot/) has been annoying IRC users on #racket, #scheme, and #emacs for years.  There's lots of little improvements on [the TODO list](https://github.com/offby1/rudybot/blob/master/TODO) and [the issue tracker](https://github.com/offby1/rudybot/issues?state=open); [the primary author](https://plus.google.com/110719264043637716066/) will be attending.