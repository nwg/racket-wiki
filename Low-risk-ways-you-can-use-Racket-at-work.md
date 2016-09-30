Wow! Racket has so many features, a full-featured **functional** and **[object-oriented](http://www.ccs.neu.edu/home/matthias/Thoughts/Programming_with_Class_in_Racket.html)** language with powerful [macro](http://www.greghendershott.com/fear-of-macros/) facilities, gradual typing and a static type checker. (It is safe and fun!)

# But how can you use Racket a work?

_Here are some low risk examples and suggestions for people to get stuff done with racket._

Use Racket (& DrRacket) ...
 1.  ... to [validate NHS numbers](https://github.com/spdegabrielle/check-nhs-number) in a dataset
 1.  ... for [parsing html pages](http://www.neilvandyke.org/racket/html-parsing/): 
 1.  ... for [Parsing CSV](http://www.neilvandyke.org/racket/csv-reading/)
 1.  ... for making cool [Presentations](http://docs.racket-lang.org/slideshow/index.html)
 1.  ... to make GUI apps (I made one to share the NHS number checker - see below)
 1.  ... to play with web services...(must provide example)
 1.  ... for diagramming and visualization
 1.  ... for accessing web-based data stores 
(Please add more)


PS You can also user Racket for creating languages, web applications, deep learning, rocket surgery, 3D, games, livecoding, ZeroMQ and making pretty pictures.

***

All credit due to 'scottw' at https://fsharpforfunandprofit.com/posts/low-risk-ways-to-use-fsharp-at-work-5/

***
## NHS Number checker
Use DrRacket. Click Racket>Create Executable

`#lang racket/gui
(define f (new frame% [label "nhs number check"]))
(send f show #t)
(define number-to-check (new text-field%   (label "Text")
                        (parent f)
                        (init-value "6666666666")))
(define (calculate-nhs-number-check-digit list-of-digits)
  (let ((c (- 11 (modulo (apply + (map * list-of-digits '(10 9 8 7 6 5 4 3 2))) 11))))
    (cond
      [(eq? c 11) 0]
      [(eq? c 10) #f] ;invalid
      [else c]
      )))

(define (valid-nhs-number? list-of-digits)
  (and (last list-of-digits)
  (equal? 
   (calculate-nhs-number-check-digit (take list-of-digits 9))
   (last list-of-digits)
   )))

(define (get-num-as-lon) (map (λ (c) (string->number (list->string (list c))))
               (string->list (send number-to-check get-value))))
(define result (new message%	 
   	 	[label "aaa"]	 
   	 	[parent f]))
(define check-it-now (λ (c e ) (send result set-label
                                     (format "~a" (valid-nhs-number? (get-num-as-lon))))))
(define check-button (new button% [label "Check"] [callback check-it-now][parent f]))


`



