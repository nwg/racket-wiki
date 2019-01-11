#### How to generate a rotating key-value, which changes at some arbitrary interval.

Here the daily-key is a simple random number, available at module level. You can plug in a better Artifact from above to create a more useful n-bit key.

The **(sync...)** function blocks until **(alarm-evt...)** is ready at next-alarm milliseconds (here arbitrarily set for 3 am). Then daily-key is mutated, and a new **(sync...)** call blocks until tomorrow at the same time.

secure-key-generation uses the **on-errror-resume-next** Artifact from above.


```racket
(provide daily-key
         start-key-generation
         secure-key-generation)

(define daily-key null)
(define key-thread null)

(define (start-key-generation)
  (unless (thread? key-thread) ;protect against reinitializing key-thread
    (set! daily-key (random 255))
    (set! key-thread (thread (λ _ 
                               (letrec ((next-alarm (λ _ (let* ((milliseconds-per-day (* 24 3600 1000))
                                                                (now (current-date))
                                                                (hour (date-hour now))
                                                                (3am-ms (* 1000 (find-seconds 0 0 3 
                                                                                              (date-day now)
                                                                                              (date-month now)
                                                                                              (date-year now)
                                                                                              #t))))
                                                           (if (hour . < . 3) 
                                                               3am-ms
                                                               (+ 3am-ms milliseconds-per-day)))))
                                        (rfc (λ _ (begin (sync (alarm-evt (next-alarm))) 
                                                         (set! daily-key (random 255))
                                                         (rfc)))))
                                 (rfc)))))))

(define (secure-key-generation)
  (on-error-resume-next
   (kill-thread key-thread)
   (set! key-thread null)
   (set! daily-key null)))
```
#### AJAX: How to build a response to an HTTPXmlRequest

Note: the correct **MIME-type** is important to get the browser to understand what you're sending over in the body of the response.

Client-side convention with respect to setting up client AJAX continuation seems to be to at least check the **message-field** equal to "OK", so be aware of this. 

In addition to this code, You still need to send the reponse back to the client via one of Jay McCarthy's primitives such as **send/suspend/dispatch** (if _stateless_), or **send/back** (if _stateful_).

```racket
#|
USAGE: 
(define res (make-xml-response `(xml "victory!")))
(call-with-output-string (response-output res))
-> "<xml>victory!</xml>"

|#
#lang racket
(require  xml
          web-server/servlet-env
          web-server/http/response-structs
          web-server/http/request-structs)

;; or just use #lang web-server and (require xml), if that's easier for you

(define (make-xml-response  #:code [code 200]
                            #:message [message #"OK"]
                            #:seconds [seconds (current-seconds)]
                            #:mime-type [mime-type #"text/xml charset=utf-8"]
                            #:headers [headers (list (make-header #"Cache-Control" #"no-cache"))]
                            content)
  (response/full code message seconds mime-type headers (list (string->bytes/utf-8 (xexpr->string content)))))
```

