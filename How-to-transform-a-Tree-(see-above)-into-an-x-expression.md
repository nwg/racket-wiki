#### How to transform a Tree into an x-expression

(see [[How to Build a Context-Free Grammar with Racket's unique Recursive Contract System]])

This converts the **beautiful tree notation possible in Racket** into the **ugly, verbose representation** necessary to send hierarchical structures to other computational environments with no respect for beauty, symmetry nor notational elegance.

```racket
(require xml)

(define tree/c
  (flat-rec-contract
   tree
   (or/c symbol?
        (listof symbol?)
        (cons/c symbol? (listof tree)))))

(define atom?
  (lambda (x)
    (and (not (pair? x)) (not (null? x)))))

(define/contract (tree->xexpr tree)
  (tree/c . -> . xexpr/c)
  (letrec ((parent-proc (λ (subtree)
                          (cond
                            [(atom? (car subtree)) `(div ((id ,(symbol->string (car subtree)))) ,@(child-proc (cdr subtree)))])))
           (child-proc (λ (subtree)
                          (cond 
                            [(null? subtree) '("")]
                            [(symbol? (car subtree)) (cons `(div ((id ,(symbol->string (car subtree)))) "")  (child-proc (cdr subtree)))]
                            [(cons? (car subtree)) (cons (parent-proc (car subtree)) (child-proc (cdr subtree)))]))))
      (parent-proc tree)))

#|
USAGE
(display (xexpr->string 
          (tree->xexpr '(S1 S2 (S3 (S3-1 S3-1-1 S3-1-2) S3-2) S4))))

RETURNS 

<div id="S1">
     <div id="S2"></div>
     <div id="S3">
        <div id="S3-1">
             <div id="S3-1-1"></div>
             <div id="S3-1-2"></div>
        </div>
        <div id="S3-2"> </div>
     </div>
     <div id="S4"></div>
</div>

|#


```

