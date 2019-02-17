The Racket _language development toolchain_ includes the Racket language(s), command line tools, IDE and a range of packages to support developing languages.

The following page attempts to bring together resources for language developers.

## Learning 
* _'[Beautiful Racket](https://beautifulracket.com): Make your own programming languages with Racket'_ by Matthew But­t­er­ick (book)
* [The Racket Guide: (17) Creating Languages](https://docs.racket-lang.org/guide/languages.html)
* [Programming Languages: Application and Interpretation](http://cs.brown.edu/courses/cs173/2012/book/) with the  
[PLAI Typed Language](https://docs.racket-lang.org/plai-typed/index.html)

## Examples
[Example languages built on or with the Racket toolchain](https://docs.google.com/spreadsheets/d/1K4IbX0OH8pz1qebG5lIaQynFIFAO2vqBA8EuCClRSSI)

## Videos
* [Building languages in an afternoon](https://youtu.be/TfehOLha-18)
* [#lang overscan: Transform live video streams with code and a REPL!!](https://youtu.be/2aOqaE6oByA)
* Building Languages in Racket  [video](https://youtu.be/y1rOWZkALto) [code](http://www.cs.utah.edu/plt/scratchy/)  (tutorial at Racket-Con 2012)
* <https://youtu.be/3N__tvmZrzc?t=2412> <http://cs.brown.edu/courses/cs173/2012/Videos/>


## Toolchain   

* **IDE (DrRacket)**, including 
  * [Macro Stepper(Macro Debugger)](https://docs.racket-lang.org/macro-debugger/index.html) to inspect Macro Expansion
  * Support for [Adding Languages to DrRacket](https://docs.racket-lang.org/tools/adding-languages.html#%28part._.Adding_.Arbitrary_.Languages_to_.Dr.Racket%29)
  * **[Macro]** [`Todo List`](https://docs.racket-lang.org/todo-list/index.html) DrRacket plugin 'intended for use with cooperating languages, especially statically typed languages and proof assistants'.

* [The C Foreign Function Interface](https://docs.racket-lang.org/foreign/index.html)
  * _The ffi/unsafe library enables the direct use of C-based APIs within Racket programs—without writing any new C code._  (e.g. The C FFI is how `#lang video` calls the `ffmpeg`.)
* [Embedding Racket](https://docs.racket-lang.org/inside/embedding.html) in larger programs.

* [Syntax Parse](https://docs.racket-lang.org/syntax/stxparse.html): _"syntax/parse helps you build robust embedded DSLs in minutes"_(quote from [slides](https://con.racket-lang.org/2016/king.pdf) for [Building languages in an afternoon](https://youtu.be/TfehOLha-18)) (See also [Syntax Parse Examples](https://docs.racket-lang.org/syntax-parse-example/index.html))

## languages 
* [`lang #` Rosette](https://docs.racket-lang.org/rosette-guide/ch_getting-started.html) to make a _solver-aided domain-specific language_
* [The `turnstile` language](https://docs.racket-lang.org/turnstile/) _"[...]aims to help Racket programmers create **typed languages**. It does so with extensions of Racket’s macro-definition forms that facilitate implementation of type rules alongside normal macro code."_ 

* **Lexers and parsers** _(easily provide a syntax suitable to the task or audience)_
  * [lex- and yacc-style lexer and parser generators](https://docs.racket-lang.org/br-parser-tools/index.html) supporting generating both [LALR(1) Parsers](https://docs.racket-lang.org/br-parser-tools/LALR_1__Parsers.html) and [Context-Free Parsers](https://docs.racket-lang.org/br-parser-tools/Context-Free_Parsers.html) with functionality to [convert _`C-language`_ `yacc` or `bison` grammars](https://docs.racket-lang.org/br-parser-tools/Converting_yacc_or_bison_Grammars.html)
  * [recursive descent parser 'The [Racket] Reader'](https://docs.racket-lang.org/reference/reader.html)
  * [PEG parser generator](https://docs.racket-lang.org/peg/index.html) 

> I have not included functionality of Racket as a General Purpose language. Please see the [Racket Guide](https://docs.racket-lang.org/guide/index.html), [Racket Reference Manual](https://docs.racket-lang.org/reference/index.html), the [Documentation](https://docs.racket-lang.org/index.html) and [Packages respository](https://pkgs.racket-lang.org/) 

## Documentation
* Macros 
  * [Intro to macros](https://docs.racket-lang.org/guide/macros.html)  (or start with [Fear of Macros](http://www.greghendershott.com/fear-of-macros/): A practical guide to Racket macros by Greg Hendershott.
)  
  * [Macros in depth](https://docs.racket-lang.org/reference/Macros.html)  
  * [Syntax-Parse](https://docs.racket-lang.org/syntax/stxparse.html): introduction to writing robust macros with syntax-parse and syntax classes
  * [Syntax Parse Examples](http://docs.racket-lang.org/syntax-parse-example/index.html)
  * [Racket syntax model](https://docs.racket-lang.org/reference/syntax-model.html)
  * [Making new languages](https://docs.racket-lang.org/guide/hash-languages.html)

## examples

* [[Racket-Languages]] (a list curated for learning purposes)
* [`#lang` in the documentation](http://docs.racket-lang.org/search/index.html?q=H%3A) 
 
## Papers
[A Programmable Programming Language](https://cacm.acm.org/magazines/2018/3/225475-a-programmable-programming-language/fulltext) by Matthias Felleisen, Robert Bruce Findler, Matthew Flatt, Shriram Krishnamurthi, Eli Barzilay, Jay McCarthy, Sam Tobin-Hochstadt. Communications of the ACM, March 2018, Vol. 61 No. 3, Pages 62-71. DOI 10.1145/3127323

[Creating Languages in Racket](https://cacm.acm.org/magazines/2012/1/144809-creating-languages-in-racket/fulltext) by Matthew Flatt. Communications of the ACM, January 2012, Vol. 55 No. 1, Pages 48-56. DOI 10.1145/2063176.2063195