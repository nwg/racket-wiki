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
;; Get a URL's entity, being sure to close the port.
(require net/url)
(call/input-url (string->url "http://www.google.com")
                get-pure-port
                port->string)

;; Get a URL's headers and entity, being sure to close the port.
(require net/url)
(define-values (headers entity)
  (call/input-url (string->url "http://www.google.com")
                  get-impure-port
                  (lambda (in)
                    (values (purify-port in)
                            (port->string in)))))
```

##### generate a n-byte key for use in MAC authentication (like HMAC-SHA1)
```racket
;usage (generate-authenticator-key 32) -> returns 256-bit key
(define/contract (generate-authenticator-key key-len)
  (-> exact-positive-integer? bytes?)
  (list->bytes (build-list key-len (λ _ (random 255)))))
```

##### How to generate a Message Authentication Code (MAC) and authenticate a signed message.

This would be useful for creating the "Unforgeable Authenticator Cookie", discussed in section 4.1 of the MIT 
Cookie Eater's recommendations (see: "Do's And Don'ts of Client Authentication on the Web", Fu et al)

Note: Uses generate-authenticator-key from the preceding Artifact.

```racket
(require web-server/stuffers/hmac-sha1)

;use 128-bit key
(define *private-key* (generate-authenticator-key 16))

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
This code creates an unhygenic macro which will execute an arbitrary number of procedures 
while ignoring errors thrown.

It most closely resembles Microsoft's "On Error Resume Next", in that it will 
sequentially execute a number of potentially error-causing statements
_without allowing control-flow to branch_.

Many, including Matthias F. strongly believe that Racket's dynamic-wind is the correct primitive 
to use instead of this macro. 

```racket
#|
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
           
#### Parsing libpcap files

This is a quick hack for parsing libpcap files (the standard format used by packet-capturing programs, e.g. wireshark) into packets. (John Clements)

```racket
(define (file->packets file)
  (define pcap-bytes (file->bytes file))
  
  (define global-header (subbytes pcap-bytes 0 (* 6 4)))
  
  (define packets
    (let loop ([offset 24])
      (cond [(< offset (bytes-length pcap-bytes))
             (define pcaprec-header (subbytes pcap-bytes
                                              offset
                                              (+ offset 16)))
             (define captured-len (integer-bytes->integer pcaprec-header
                                                          #f #f
                                                          8 12))
             (define packet-len (integer-bytes->integer pcaprec-header
                                                        #f #f
                                                        12 16))
             (when (not (= captured-len packet-len))
               (fprintf (current-error-port)
                        "warning: captured only ~v bytes of packet with ~v bytes\n"
                        captured-len packet-len))
             (printf "packet len: ~v\n" captured-len)
             (cons 
              (list pcaprec-header
                    (subbytes pcap-bytes (+ offset 16)
                              (+ offset 16 captured-len)))
              (loop (+ offset 16 captured-len)))]
            [else empty]))))
```

    
#### Directly calling the OpenSSL executable from Racket 

This example generates a 1024-bit RSA key in PEM format 

Idea courtesy of Neil Van Dyke. Control flow suggested by Neil Van Dyke, Robby Findler and Eli Barzilay. 

```racket
(parameterize ([current-input-port (open-input-string "")])
  (with-output-to-string (λ _(system* (build-path "c:" "openssl-win32" "bin" "openssl.exe")
                                      "genrsa" 
                                      "1024"))))
```

#### More OpenSSL: generating an HMAC-SHA1 digest 
```racket
;;returns the string "(stdin)= 5df23ffdf57d5d925f150c885d64bee2eaf55a43\n"

(parameterize ([current-input-port (open-input-string "We are Spinal Tap!")])
  (with-output-to-string (λ _ (system* (build-path "c:" "openssl-win32" "bin" "openssl.exe")
                                      "dgst" 
                                      "-sha1"
                                      "-hex"
                                      "-hmac"
                                      #"mysecretkey"))))
```

#### How to generate a changing key-value, which changes at some arbitrary chronological interval.

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
#### Contract System

I think Racket's contract system fails to get enough love from the community. 

The recursive definitions are mind blowing.

You can build a syntactical parser out of it.  

For example, here's a context-free grammar of a binary tree written using the contract system. A parent node is the first element of a list. A child node is a cons'd element in the same list

Its like getting a free goal-seeker for Christmas.  [ok, it can't generate substitutions, but it can provide answers to existential queries!]

```racket
(define tree/c
  (flat-rec-contract
   tree
   (or/c symbol?
        (listof symbol?)
        (cons/c tree tree))))

#|
usage 
S1
(tree/c 'S1) ;-> #t

S1
|
S2
(tree/c '(S1 S2)) ;-> #t

   __ S1___
   |   |   |    
   S2  S3  S4  
     __|__
    |     |
   S3-1  S3-2
  __|__
 |     |
 S3-1-1  S3-1-2   

(tree/c '(S1 S2 (S3 (S3-1 S3-1-1 S3-1-2) S3-2) S4)) ;->#t

|#
```racket



###### Thanks to Zack Galler for the suggestion.