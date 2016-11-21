As part of the [[Inside Racket Seminar]] series, on November 17th, 2016, [Sam Tobin-Hochstadt](http://samth.github.io) spoke about the [Racket Pattern Matcher](https://github.com/racket/racket/tree/master/racket/collects/racket/match) library with [Jay McCarthy](http://jeapostrophe.github.io).

The archived YouTube live event is [here](https://www.youtube.com/watch?v=IikGK8XP5_Q).

The seminar is oriented on the details of the implementation and is not an introduction to Racket pattern matching.

### Papers on pattern matching

* [Compiling pattern matching](https://books.google.com/books?hl=en&lr=&id=AiMwYZs-TGkC&oi=fnd&pg=PA368&ots=ptmi1IsgX5&sig=6GJVKFI_KLpyxYqS-pt6FtYS2ZQ#v=onepage&q&f=false), by Lennart Augustsson, FPCA 1985. The original paper on the compilation technique used by `match`
* [Optimizing pattern matching](http://dl.acm.org/citation.cfm?id=507641&CFID=693592570&CFTOKEN=26018742), by Fabrice Le Fessant and Luc Maranget, ICFP 2001. The paper the `match` implementation is based on.
* [Compiling pattern matching to good decision trees](http://dl.acm.org/citation.cfm?id=1411311&CFID=693592570&CFTOKEN=26018742) by Luc Maranget, ML Workshop 2005. About a different technique, but with some heuristics that `match` uses.
* [Extensible pattern matching in an extensible language](https://arxiv.org/abs/1106.2578), by Sam Tobin-Hochstadt A paper about how match expanders work. 
