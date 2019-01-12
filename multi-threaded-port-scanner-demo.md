## multi-threaded port scanner demo


```
#lang racket
;; Code from Why I Like PLT Scheme by Jacob Matthews
;; http://www.kuro5hin.org/story/2004/3/17/93442/8657
;; archived as https://web.archive.org/web/20050205000754/http://www.kuro5hin.org/story/2004/3/17/93442/8657
;; minor changes to port to Racket 7.1
(module+ test
  (require rackunit))

; scan : string[hostname] (listof int) -> listof (list int string)
; gives the number and well-known service name of each port in the given
; list that is open on the given host
(define (scan host ports)
  (map 
   (lambda (p) (list p (port->name p)))
   (open-ports host ports)))

(define (range low high)
  (cond
    [(> low high) null]
    [else (cons low (range (+ low 1) high))]))

(require racket/contract)

(provide/contract 
 (scan (string? (listof natural-number/c) 
                . -> . 
                (listof (list/c natural-number/c string?)))))

;(require (lib "list.ss")) ; for filter
 
; open-ports : string[hostname] (listof int) -> (listof int)
; returns the sublist of numbers that represent open ports on the
; given host, performing all checks concurrently
(define (open-ports host ports)
  (filter (lambda (x) (not (eq? 'closed x)))
          (threaded-map
           (lambda (port) (if (can-connect? host port) port 'closed)) 
           ports)))

; can-connect? : string[hostname] number -> bool
; determines if the host is listening on the given port
(define (can-connect? host port)
  (with-handlers ([exn:fail:network? (lambda (e) #f)])
    (let-values ([(ip op) (tcp-connect host port)])
      (close-input-port ip) (close-output-port op) #t)))

; threaded-map : (X -> Y) * (listof X) -> (listof Y)
; maps the given function over the given list with each computation 
; done in parallel
(define (threaded-map f l)
  (let ((cs (map (lambda (x) (make-channel)) l)))
    (for-each (lambda (x c) (thread (lambda () (channel-put c (f x))))) l cs)
    (map channel-get cs)))

(require  net/url) ; for get-pure-port and string->url
 
(define NAMES
  (let ([ip (if (file-exists? "/etc/services")
                (open-input-file "/etc/services")
                (get-pure-port (string->url "http://www.iana.org/assignments/port-numbers")))]
        [nametable (make-hash)])
    (while m (regexp-match #px"([^ \n]+)[\\W]+([0-9]+)/tcp[ \t]+([^\r\n])" ip)
           (hash-set! nametable (string->number (bytes->string/utf-8 (list-ref m 2))) (list-ref m 1)))
    nametable))
 
(define (port->name p) (hash-ref! NAMES p (lambda () "unknown")))

(define-syntax (while stx)
  (syntax-case stx ()
    [(_ var test body)
     (identifier? #'var)
     #'(let loop ((var test))
         (when var body (loop test)))]))

(module+ test
  ;; Any code in this `test` submodule runs when this file is run using DrRacket
  ;; or with `raco test`. The code here does not run when this file is
  ;; required by another module.
  (scan "www.lnwh.nhs.uk" (range 1 100))

  )

(module+ main
  ;; (Optional) main submodule. Put code here if you need it to be executed when
  ;; this file is run using DrRacket or the `racket` executable.  The code here
  ;; does not run when this file is required by another module. Documentation:
  ;; http://docs.racket-lang.org/guide/Module_Syntax.html#%28part._main-and-test%29

  )
```
