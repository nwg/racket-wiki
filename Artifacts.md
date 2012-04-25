This page captures useful code snippets that are too small to be a Planet package. 

##### Specifying a HMAC-SHA1 stuffer for the stateless web-server

```racket
#:stuffer (stuffer-chain
            serialize-stuffer
            (stuffer-compose base64-stuffer
                             (HMAC-SHA1-stuffer #"mysupersecretkey")))
```

##### Split a string into lines

```racket
(regexp-split "\n+" str)
```

##### Fetch the contents of a URL

```racket
(require net/url)
(port->string (get-pure-port (string->url "https://www.google.com")))
```
##### generate a n-byte key for use in MAC authentication (like HMAC-SHA1)
```racket
;usage (generate-authenticator-key 128) -> returns 128-byte key
(define/contract (generate-authenticator-key key-len)
  (-> exact-positive-integer? bytes?)
  (list->bytes (build-list key-len (λ _ (random 255)))))
```

##### How to generate a Message Authentication Code and authenticate a signed message.

```racket
#|
This would be useful for creating an "Unforgeable Authenticator Cookie", per the MIT 
Cookie Eater's recommendations (see: "Do's And Don'ts of Client Authentication on the Web", Fu at para 4.1)

Uses generate-authenticator-key from the preceding Artifact.

|#

(require web-server/stuffers/hmac-sha1)

(define *private-key* (generate-authenticator-key 128))

(define *signed-message* (let* ((plaintext #"We are Spinal Tap!")
                                (MAC (HMAC-SHA1 plaintext *private-key*)))
                           (bytes-append MAC plaintext)))
  
;;now we lose custody of *signed-message* by sending it to the client...

;;and now we get *signed-message* back and attempt to authenticate it

(let ((received-MAC (subbytes *signed-message* 0 20))
      (received-plaintext (subbytes *signed-message* 20)))
  (if (bytes=? received-MAC
               (HMAC-SHA1 received-plaintext 
                          *private-key*))
      "Message is authentic and not forged"
      "Message has been forged"))

```
##### Controversial code: cleaning up state on exit, when errors are expected
```racket
#|
Explanation: this code creates an unhygenic macro which will execute an arbitrary number of procedures 
while ignoring errors thrown.

it most closely resembles Microsoft's "On Error Resume Next",
in that it will execute a number of potentially error-causing statements
****without allowing control-flow to branch***.**

Many, including Matthias F. strongly believe that Racket's dynamic-wind is the correct primitive 
to use instead of this macro. 

USAGE: 
(define (myerror n)
  (raise (exn:fail (format "threw error ~A\n" n) (current-continuation-marks))))

(on-error-resume-next (myerror 1) (myerror 2) (myerror 3) (myerror 4))


|#
(require mzlib/defmacro)

(define-macro (on-error-resume-next . (fn . rest))
  (let ((out (gensym))
        (k   (gensym)))
  `(let* ((,out #f))
    (with-handlers ([exn:fail? (lambda (exn) (printf "~A\n" (exn-message exn)) (,out))])
      ,@(map (lambda (f) `(let/cc ,k (set! ,out ,k) ,f)) (cons fn rest))))))
```
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
           


###### Thanks to Zack Galler for the suggestion.