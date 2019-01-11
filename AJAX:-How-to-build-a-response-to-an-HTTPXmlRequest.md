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

