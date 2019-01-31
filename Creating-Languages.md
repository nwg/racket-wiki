The Racket _language development toolchain_ includes the racket language(s), [recursive descent parser](https://docs.racket-lang.org/reference/reader.html), [lex- and yacc-style lexer and parser generators](https://docs.racket-lang.org/br-parser-tools/index.html) and [PEG parser generator](https://docs.racket-lang.org/peg/index.html)] command line tools and IDE.

## Examples
[Example languages built on or with the racket toolchain](https://docs.google.com/spreadsheets/d/1K4IbX0OH8pz1qebG5lIaQynFIFAO2vqBA8EuCClRSSI)

## Videos
* [Building languages in an afternoon](https://youtu.be/TfehOLha-18)
* [#lang overscan: Transform live video streams with code and a REPL!!](https://youtu.be/2aOqaE6oByA)
* Building Languages in Racket  [video](https://youtu.be/y1rOWZkALto) [code](http://www.cs.utah.edu/plt/scratchy/)  (tutorial at Racket-Con 2012)

## Toolchain   
> I've tried to include the parts of the Racket language development toolchain specific or important to language development. e.g. The C FFI is a key part of how `#lang video` works with the `ffmpeg` library.

> I have not included functionality of Racket as a General Purpose Multi-Paradigm language, or the broad range of Racket libraries. Please see the [Racket Guide](https://docs.racket-lang.org/guide/index.html), [Racket Reference Manual](https://docs.racket-lang.org/reference/index.html), the [Documentation](https://docs.racket-lang.org/index.html) and [Packages respository](https://pkgs.racket-lang.org/) 

* **Racket language** and libraries, including 
  * [Syntax Parse](https://docs.racket-lang.org/syntax/stxparse.html) to support developing more sophisticated macros with integrated error support: Macros that use syntax-parse automatically generate error messages based on descriptions and messages embedded in the macro’s syntax patterns. (See [Syntax Parse Examples](https://docs.racket-lang.org/syntax-parse-example/index.html))
  * [Typed Racket]() with static type checking, type classes, and gradual typing to support grwign MVP's into large stable systems. 
  * [RackUnit](https://docs.racket-lang.org/rackunit/index.html)) unit-testing framework, [Clover: test coverage tool]
(https://docs.racket-lang.org/cover/index.html) & [Overeasy: Racket Language Test Engine](https://docs.racket-lang.org/overeasy/index.html)
* **Lexers and parsers**
  * [lex- and yacc-style lexer and parser generators](https://docs.racket-lang.org/br-parser-tools/index.html) including 
    * [Lexers](https://docs.racket-lang.org/br-parser-tools/Lexers.html)
    * [LALR(1) Parsers](https://docs.racket-lang.org/br-parser-tools/LALR_1__Parsers.html)
      * [Converting _`C-language`_ `yacc` or `bison` Grammars](https://docs.racket-lang.org/br-parser-tools/Converting_yacc_or_bison_Grammars.html)
    * [Context-Free Parsers](https://docs.racket-lang.org/br-parser-tools/Context-Free_Parsers.html)
  * [recursive descent parser](https://docs.racket-lang.org/reference/reader.html)
  * [PEG parser generator](https://docs.racket-lang.org/peg/index.html)] 
* [extensible] [**command line tools**](https://docs.racket-lang.org/raco/index.html), including, but not limited to; 
  * [Compiling Source to Bytecode](https://docs.racket-lang.org/raco/make.html)
  * [Creating](https://docs.racket-lang.org/raco/exe.html) & [Sharing Stand-Alone Executables](https://docs.racket-lang.org/raco/exe-dist.html)
  * [Package Management](https://docs.racket-lang.org/pkg/index.html) 
  * [Installation Management](https://docs.racket-lang.org/raco/setup.html) 
  * [Working with C Code](https://docs.racket-lang.org/raco/ctool.html) including **[embedding the Racket run-time system in larger programs and extending Racket directly with C-implemented libraries](https://docs.racket-lang.org/inside/index.html)**
  * [Run tests](https://docs.racket-lang.org/raco/test.html) (using [`test` submodule](https://docs.racket-lang.org/guide/Module_Syntax.html?#%28part._main-and-test%29) and [RackUnit](https://docs.racket-lang.org/rackunit/index.html))
  * [Building Documentation](https://docs.racket-lang.org/raco/scribble.html) created with [scribble/manual](https://docs.racket-lang.org/scribble/plt-manuals.html)
* **IDE (DrRacket)**, including 
  * [Macro Stepper(Macro Debugger)](https://docs.racket-lang.org/macro-debugger/index.html) to inspect Macro Expansion
  * Support for [Adding Languages to DrRacket](https://docs.racket-lang.org/tools/adding-languages.html#%28part._.Adding_.Arbitrary_.Languages_to_.Dr.Racket%29)
  * macro [`Todo List`](https://docs.racket-lang.org/todo-list/index.html) DrRacket plugin 'intended for use with cooperating languages, especially statically typed languages and proof assistants'.

## Workflow

DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT

Options for building your language
* extend Racket via libraries (not a language)
* extend Racket via macros (extending the language)
* provide a combination of library and/or macro language extensions and a subset of Racket (a new language closely related to Racket)
* provide a combination of library and/or macro language extensions, removing racket language forms and functions (a new language)




1. Define language 
  * what does it do
  * what syntax will it use
  * (define and validate language with Redex ?)

2. build _forms_ (using macros)

4. build parser with `racket reader` or `peg` or generate parser with `[parser tools](http://docs.racket-lang.org/br-parser-tools/index.html)`
5. ??


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