This page lists [Racket](http://www.racket-lang.org) projects which are feasible for people who don't
have a lot of experience with the Racket code base. They're mostly
small, self contained, and would be extremely useful. Some involve
writing a new library that would be useful to lots of other people, and
some help fix or clean up some aspect of the existing Racket code base.

The best place to ask for help with any of these is on the [users
mailing list](http://racket-lang.org/community.html).

Remember the [Racket Documentation](https://docs.racket-lang.org/index.html) is your friend for solving problems, [DrRacket is a powerful IDE](http://docs.racket-lang.org/drracket/interface-essentials.html) that can help write and debug your code (and [macros](http://docs.racket-lang.org/macro-debugger/index.html#%28part._.Using_the_.Macro_.Stepper%29)), and don't forget to check the [Racket Package Repository](https://pkgs.racket-lang.org/) for packages that can help you complete your project.

Don't forget to take a peek at [[Recreational Programming]] for more ideas.

These are self-contained projects.  Just create a new github repository,
and start hacking.  When you have something that works, release it on the
[package catalog](http://pkgs.racket-lang.org/). To get started with packages, take a look at its [documentation](http://www.cs.utah.edu/plt/snapshots/current/doc/pkg/index.html).

* Implement a Rosetta code task: http://rosettacode.org/wiki/Reports:Tasks_not_implemented_in_Racket
  - You could also re-implement or improve an existing Racket solution
* Implement mini versions of classical programs (can be used as extended examples on the web site):
  - Notepad using racket/gui
  - Paint 
  - Calculator
* Data structures: [hash array mapped trie](http://en.wikipedia.org/wiki/Hash_array_mapped_trie), [2-3 finger trees](http://en.wikipedia.org/wiki/Finger_tree), other [purely functional data structures](http://cstheory.stackexchange.com/questions/1539/whats-new-in-purely-functional-data-structures-since-okasaki) (some already implemented [here](https://github.com/takikawa/tr-pfds)).
* Code for doing OAuth
  - Now available [here](https://github.com/veer-public/OAuth-2.0)
  - Also available as part of ryanc's webapi PLaneT package.
* Write bindings for libgit
  - Work started [here](https://github.com/jarnaldich/racket-git)
* Write bindings to Authorize.Net
* Write libraries to interact with Wii Remotes
  - [Technical details](http://wiibrew.org/wiki/Wiimote) on the Wiimote
  - [wiiuse](http://sourceforge.net/projects/wiiuse/) has code for the Wiimote's protocol, as well as Win/Linux bluetooth code
  - Mac OSX [Bluetooth Dev info](http://developer.apple.com/library/mac/#documentation/DeviceDrivers/Conceptual/Bluetooth/BT_Intro/BT_Intro.html)
* Write libraries to interact with game controllers
  - This exists on for [Mac OS X](https://github.com/get-bonus/get-bonus/blob/master/exp/joystick.rkt), but an interface should be normalized and available across platforms.
  - maybe use [libsdl](http://www.libsdl.org/)?
* Write bindings to various Google APIs
  - Authentication would be useful
  - Other interesting things: docs (esp. around spreadsheets), maps
* Write bindings to the Github API
  - Basic binding available [here](https://github.com/eu90h/racket-github-api)
* Write bindings to the Twitter APIs
* Write bindings to the Facebook APIs
* Write bindings to Amazon AWS.
  - [Eric Hanchrow](https://github.com/offby1/doodles/tree/master/plt-scheme/web/amazon) has some first steps which might be inspirational.
  - a typed/racket effort by [Ray Racine](https://github.com/RayRacine/knozamalib/tree/master/src/racket/aws) which is actively being developed.
  - Greg Hendershott has untyped Racket code for the S3, SDB, SES, SNS, SQS, CloudWatch, and other services [Github](https://github.com/greghendershott/aws). 
* Write XMPP bindings
   - A starting point can be found [here](https://github.com/zzkt/gibberish)
* Bindings for a text to speech engine
* IRC log highlighter. Starting points :
   - [cosmez/racket-log-highlighter](https://github.com/cosmez/racket-log-highlighter)
   - [fridim/pimpmylog](https://github.com/fridim/pimpmylog)
* IRC client library (can be based on the gabot code (contact [Eli](mailto:eli@barzilay.org)), which
  is better for a library than [rudybot](https://github.com/offby1/rudybot)). Jonathan Schuster has done [racket-irc](https://github.com/schuster/racket-irc).
* Bindings for Apple's Core-* Libraries
* Write a better s-exp diff tool
* Write bindings to gobject introspection
* Use the Racket examples on Rosetta Code and the snippets on the http://racket-lang.org home page to make `demo.racket-lang.org` that show cases programs and snippets written in Racket.  There's a start of explanations of the home page snippets here: https://github.com/samth/racket-examples
