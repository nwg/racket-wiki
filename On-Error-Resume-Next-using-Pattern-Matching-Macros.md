#### On Error Resume Next using Pattern Matching Macros

Allows us to sequentially execute error-throwing statements without causing control flow to branch

```racket

(define-syntax-rule (on-error-resume-next f ...)
   (let ((out #f))
     (with-handlers ([exn:fail? (lambda (exn) (printf "~A\n" (exn-message exn)) (out))])
       (let/cc k (set! out k) f) ...)))
                            
       
#| usage
(define (my-error val) (error (format "my-error ~A\n" val)))

(on-error-resume-next (my-error 1) (my-error 2) (my-error 3))
;RETURNS
my-error 1

my-error 2

my-error 3

#|

```
