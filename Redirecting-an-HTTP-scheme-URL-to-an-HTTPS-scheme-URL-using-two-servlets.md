##### Redirecting an HTTP-scheme URL to an HTTPS-scheme URL using two servlets (courtesy of Jay McCarthy)

```racket
#lang web-server
(require  web-server/servlet-env)

(define (secure-start request)
  (response/xexpr "Hello SSL-encrypted world"))

;redirect to https:
(define (insecure-start request)
    (display "in redirect\n")
    (redirect-to
     (url->string
      (struct-copy url (request-uri request)
                   [scheme "https"]
                   [host "www.mydomain.com"]
                   [port 8001]))))
  
;;secure servlet on port 8001, with server-authentication via x.509
(define secure-servlet
  (thread
   (λ ()
    (serve/servlet secure-start 
               #:stateless? #t
               #:launch-browser? #f
               #:connection-close? #t
               #:quit? #f 
               #:listen-ip #f 
               #:port 8001
               #:ssl? #t
               #:ssl-cert (build-path  "my-domain-cert.crt")
               #:ssl-key (build-path  "my-private-key.key") 
               #:servlet-path "/"))))


;; inesecure servlet on port 8000
(define insecure-servlet
  (thread
   (λ ()
    (serve/servlet
       insecure-start
       #:stateless? #t        
       #:launch-browser? #f
       #:connection-close? #t
       #:quit? #f 
       #:listen-ip #f 
       #:port 8000
      #:servlet-path "/"
      ))))

(thread-wait insecure-servlet)
(thread-wait secure-servlet)
```

