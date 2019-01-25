Racket includes a powerful macro system to extend the language or make new languages:

## Videos

*   
* 

## Toolchain   
_DRAFT_ (What you need)

* Racket
* install BNF or PEG packages as required (to build new syntax)
* 

## Workflow

1. Define language 
  * what does it do
  * what syntax will it use
  * (optional) define and validate language with Redex
2. 


## Documentation
* Macros 
  * [Intro to macros](https://docs.racket-lang.org/guide/macros.html)  (or start with [Fear of Macros](http://www.greghendershott.com/fear-of-macros/))  
  * [Macros in depth](https://docs.racket-lang.org/reference/Macros.html)  
  * [introduction to writing robust macros with syntax-parse and syntax classes](https://docs.racket-lang.org/syntax/stxparse.html)
  * [Syntax Parse Examples](http://docs.racket-lang.org/syntax-parse-example/index.html)
  * [Racket syntax model](https://docs.racket-lang.org/reference/syntax-model.html)
  * [Making new languages](https://docs.racket-lang.org/guide/hash-languages.html)

## examples

* [[Racket-Languages]] (a list curated for learning purposes)
* [`#lang` in the documentation](http://docs.racket-lang.org/search/index.html?q=H%3A) 

## Other resources

* [Fear of Macros](http://www.greghendershott.com/fear-of-macros/): A practical guide to Racket macros by Greg Hendershott.
* [Beautiful Racket](https://beautifulracket.com) 'Make your own programming languages with Racket.' by Matthew But­t­er­ick (book)

## Papers
[A Programmable Programming Language](https://cacm.acm.org/magazines/2018/3/225475-a-programmable-programming-language/fulltext) by Matthias Felleisen, Robert Bruce Findler, Matthew Flatt, Shriram Krishnamurthi, Eli Barzilay, Jay McCarthy, Sam Tobin-Hochstadt. Communications of the ACM, March 2018, Vol. 61 No. 3, Pages 62-71. DOI 10.1145/3127323

[Creating Languages in Racket](https://cacm.acm.org/magazines/2012/1/144809-creating-languages-in-racket/fulltext) by Matthew Flatt. Communications of the ACM, January 2012, Vol. 55 No. 1, Pages 48-56. DOI 10.1145/2063176.2063195
