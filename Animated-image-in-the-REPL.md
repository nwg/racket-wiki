This is done with a [snip% object](https://docs.racket-lang.org/gui/editor-overview.html#%28part._snip-example%29) 

from https://gist.github.com/alex-hhh/d6bdc9f9b671876d6726396e3c7b05c9 

```
#lang racket
(require racket/gui racket/draw pict)

(define animation-snip-class  ; create singleton object
  (make-object
   (class snip-class%
     (super-new)
     (send this set-classname "animation-snip-class"))))

(define animation-snip%
  (class snip%
    (init-field picts interval)
    (super-new)
    (send this set-snipclass animation-snip-class)

    (define a-width (for/fold ([m #f])
                              ([p picts])
                    (define w (pict-width p))
                    (if m (max w m) w)))

    (define a-height (for/fold ([m #f])
                               ([p picts])
                       (define h (pict-height p))
                       (if m (max h m) h)))

    (define index 0)

    (define (on-refresh)
      (set! index (modulo (add1 index) (length picts)))
      (define admin (send this get-admin))
      (when admin
        (send admin needs-update this 0 0 a-width a-height)))
    
    (define timer (new timer% [interval interval] [notify-callback on-refresh]))

    (define/override (copy)
      (new animation-snip% [picts picts] [interval interval]))
    
    (define/override (get-extent dc x y width height descent space lspace rspace)
      (when width (set-box! width a-width))
      (when height (set-box! height a-height))
      ;; NOTE: technically, for picts we can compute these as well
      (when descent (set-box! descent 0.0))
      (when space (set-box! space 0.0))
      (when lspace (set-box! lspace 0.0))
      (when rspace (set-box! rspace 0.0)))

    (define/override (draw dc x y . other)
      (define pict (list-ref picts index))
      (define ox (* (- a-width (pict-width pict)) 0.5))
      (define oy (* (- a-height (pict-height pict)) 0.5))
      (draw-pict pict dc (+ x ox) (+ y oy)))

  
    ))


(define sample-picts
  (list
   (colorize (circle 10) "red")
   (colorize (rectangle 20 20) "blue")
   (text "hello")))

(new animation-snip% [picts sample-picts] [interval 1000])
```
