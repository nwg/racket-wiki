The [getting-started](https://docs.racket-lang.org/getting-started/index.html) guide covers installation, and learning resources for both beginners and experienced programmers. (Don't forget to set your [[Path]])!

## Useful resources:  
* [How to Program Racket: a Style Guide](http://docs.racket-lang.org/style/index.html)
* [Racket Cheat Sheet](http://docs.racket-lang.org/racket-cheat/index.html) 
* [Beautiful Racket: an intro­duc­tion to language-oriented program­ming using Racket](https://beautifulracket.com) 
* [Teach Yourself Racket](https://cs.uwaterloo.ca/~plragde/flaneries/TYR/)(TYR): is a rapid introduction to the basics of programming in full Racket, intended for mature programmers.  
* [Learning Racket](https://github.com/lojic/LearningRacket) by Brian Adkins of Lojic Technologies
* [[IDE's and text editors]] 
* [Tutorial: Creating a Package](https://blog.racket-lang.org/2017/10/tutorial-creating-a-package.html) by Stephen Chang
  * [Getting Started with packages](https://docs.racket-lang.org/pkg/getting-started.html)
* [Racket dev workflow](https://www.greghendershott.com/2014/11/racket-workflow.html) by [Greg Hendershott](https://www.greghendershott.com/index.html)

Hot Tip: Set your PATH environment variable so you can use `raco` and other Racket command line functions.

On macOS: `sudo sh -c 'echo "/Applications/Racket v7.3/bin" >> /etc/paths.d/racket'`
On Windows one of the following 
 * add the racket bin path to `Path` in 'Envi­ron­ment Vari­ables' (under System Properties, Advanced tab)
 * right click on Start menu and select Command Prompt(Admin), then `setx /m PATH "C:\my\installed\racket\bin\;%PATH%"` (restart command prompt required)
 * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment (restart windows required)

There is also a [Note to Readers with Lisp/Scheme Experience](https://docs.racket-lang.org/guide/intro.html#%28part._use-module%29) in the Racket Guide.

## First tasks 
There are various tasks you can attempt to learn Racket; 
* [[Easy bugs to fix]]
* let us know if you have trouble with the [Racket Documentation](https://docs.racket-lang.org): When you find the documentation obscure, _treat it as a documentation bug and report it_ by sending an email with your observations and suggestions to the [Racket mailing list](https://lists.racket-lang.org) or  https://groups.google.com/forum/#!forum/racket-users **This is an important way you can contribute even if you are very new to Racket**
* use http://timb.net/popular-languages.html to find incomplete rosetta-code tasks