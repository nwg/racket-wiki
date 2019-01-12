## call raco scribble --html 

A function that invokes `raco scribble` using [`(require raco/all-tools)`](http://docs.racket-lang.org/raco/command.html#%28def._%28%28lib._raco%2Fall-tools..rkt%29._all-tools%29%29)

```
(require raco/all-tools)
;;scribble-to-html : source target body
;; generate html file from scribble file
(define (scribble-to-html source target)
  (define raco-scribble-spec (hash-ref (all-tools) "scribble"))  
  (parameterize
      ([current-namespace (make-base-namespace)] ;; to allow for multiple calls
       [current-command-line-arguments (vector "--html" (path->string source))]
       [current-directory target])
    (dynamic-require (cadr raco-scribble-spec) #f)))
```