## Choosing a data structure

    DATA STRUCTURE   ACCESS       NUMBER     INDICES
    List:            sequential   Variable   not used
    Struct:          random       Fixed      names
    Vector:          random       Fixed      integer
    Growable vector: random       Variable   integer
    Hash:            random       Variable   hashable
    Splay:           random       Variable   non-integer, total order

Credit: Jens Axel Søgaard   
Source: [https://stackoverflow.com/questions/27584416/in-racket-what-is-the-advantage-of-lists-over-vectors/27589146#27589146](https://stackoverflow.com/questions/27584416/in-racket-what-is-the-advantage-of-lists-over-vectors/27589146#27589146)

## See also

* [draft notes on data structures in Racket(gist)](https://gist.github.com/alex-hhh/3cc5690a7f9c74543dab6c11344e6202), with some performance considerations. by [Alex Harsányi](https://alex-hhh.github.io/) 