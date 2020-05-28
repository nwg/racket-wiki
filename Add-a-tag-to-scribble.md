Add a tag to scribble 


```racket
#lang scribble/base

@(require
   (only-in scribble/core make-style)
   (only-in scribble/html-properties alt-tag))

@(define details-style (make-style #f (list (alt-tag "details"))))

@(define (details . arg*)
   (apply elem #:style details-style arg*))

@; -----------------------------------------------------------------------------

This is a Scribble document with a @tt{details} element.

@details{
 The @tt{alt-tag} style property can change the HTML tag that
 Scribble creates for an @tt{element} or @tt{paragraph}.

 @url{https://docs.racket-lang.org/scribble/core.html#(def._((lib._scribble%2Fhtml-properties..rkt)._alt-tag))}
}
```

nested: 

```racket
#lang scribble/base

@(require
   (only-in scribble/core make-style)
   (only-in scribble/html-properties alt-tag))

@(define details-style (make-style #f (list (alt-tag "details"))))
;summary
@(define summary-style (make-style #f (list (alt-tag "summary"))))

@(define (details summary . arg*)
   (apply elem (elem summary #:style summary-style) #:style details-style arg*))

@; -----------------------------------------------------------------------------

This is a Scribble document with a @tt{details} element.

@details["the details heading"]{
 The @tt{alt-tag} style property can change the HTML tag that
 Scribble creates for an @tt{element} or @tt{paragraph}.

@url{https://docs.racket-lang.org/scribble/core.html#(def._((lib._scribble%2Fhtml-properties..rkt)._alt-tag))}
}
```


