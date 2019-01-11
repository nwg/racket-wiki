#### How to Build a Context-Free Grammar with Racket's unique Recursive Contract System

Here's a context-free grammar of a binary tree written using the contract system. A parent node is the first symbol of a list. A child node is a cons'd s-expression in the same list

Its like getting a free goal-seeker for Christmas!  [while Racket's recursive contract system can't find substitutions, it can provide answers to existential queries!]

```racket
(define tree/c (flat-rec-contract tree
                                  (or/c symbol?
                                        (listof symbol?)
                                        (cons/c symbol? (listof tree)))))

#|
usage 

EXAMPLES: WELL-FORMED TREES

       S1 

(tree/c 'S1) ;-> #t

        S1
        |
       S2

(tree/c '(S1 S2)) ;-> #t

       S1
   ____|____
   |   |   |    
   S2  S3  S4  
     __|__
    |     |
   S3-1  S3-2
  __|__
 |     |
 S3-1-1  S3-1-2   

(tree/c '(S1 S2 (S3 (S3-1 S3-1-1 S3-1-2) S3-2) S4)) ;->#t

COUNTEREXAMPLES: MALFORMED TREES

(tree/c '((a b))) ;#->f

(tree/c '((a b) (c d))) ;#->f


|#
```
