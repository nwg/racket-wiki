This page captures useful code snippets that are too small to be a Planet package. 

[[Specifying a HMAC-SHA1 stuffer for the stateless web-server]]  
[[Split a string into lines]]  
[[Fetch the contents of a URL]]  
[[generate a n-byte key for use in MAC authentication]]  
[[How to generate a Message Authentication Code (MAC) and authenticate a signed message|generate a MAC and authenticate a signed message]]  
[[Redirecting an HTTP-scheme URL to an HTTPS-scheme URL using two servlets]]  
[[Parsing libpcap files]]  
[[Directly calling the OpenSSL executable from Racket|Directly calling OpenSSL]]  
[[OpenSSL on Amazon Linux]]  
[[On Error Resume Next using Pattern Matching Macros]]  
[[How to generate a rotating key-value, which changes at some arbitrary interval|How to generate a rotating key value]]  
[[AJAX: How to build a response to an HTTPXmlRequest]]  
[[How to Build a Context-Free Grammar with Racket's unique Recursive Contract System]]  




#### How to transform a Tree (see above) into an x-expression

This converts the **beautiful tree notation possible in Racket** into the **ugly, verbose representation** necessary to send hierarchical structures to other computational environments with no respect for beauty, symmetry nor notational elegance.

```racket
(require xml)

(define tree/c
  (flat-rec-contract
   tree
   (or/c symbol?
        (listof symbol?)
        (cons/c symbol? (listof tree)))))

(define atom?
  (lambda (x)
    (and (not (pair? x)) (not (null? x)))))

(define/contract (tree->xexpr tree)
  (tree/c . -> . xexpr/c)
  (letrec ((parent-proc (λ (subtree)
                          (cond
                            [(atom? (car subtree)) `(div ((id ,(symbol->string (car subtree)))) ,@(child-proc (cdr subtree)))])))
           (child-proc (λ (subtree)
                          (cond 
                            [(null? subtree) '("")]
                            [(symbol? (car subtree)) (cons `(div ((id ,(symbol->string (car subtree)))) "")  (child-proc (cdr subtree)))]
                            [(cons? (car subtree)) (cons (parent-proc (car subtree)) (child-proc (cdr subtree)))]))))
      (parent-proc tree)))

#|
USAGE
(display (xexpr->string 
          (tree->xexpr '(S1 S2 (S3 (S3-1 S3-1-1 S3-1-2) S3-2) S4))))

RETURNS 

<div id="S1">
     <div id="S2"></div>
     <div id="S3">
        <div id="S3-1">
             <div id="S3-1-1"></div>
             <div id="S3-1-2"></div>
        </div>
        <div id="S3-2"> </div>
     </div>
     <div id="S4"></div>
</div>

|#


```
#### Web Server: Creating an Interface Definition Language (IDL) between an HTTP-request and Racket code, Part I

**Discussion:** an HTTP request contains name/value bindings passed as byte-strings.

Maybe.

_**Sad, Tragic and Unfortunate Outcome space:**_

**1)** Bindings your Racket code expects could be missing. 

**2)** optional bindings might be present or absent

**3)** The underlying values might not be interpretable as the value types you expect (just when you expect an integer, the binding-value is "_frobnitzzz_")

**4)** The actual values passed might be outside the domain (i.e. allowable values) the Racket code works on


We want to catch these problems using the contract system before we create a server error. We use _functional composition_ to create **make-idl**, which will take four arguments:

Recall that in _composition_, the first function to execute is the rightmost argument, with its return value(s) being passed to the function-argument on its left

So reading **(make-idl....)** from right to left:

**binding-name**: the name of the binding we expect in the HTTP request

**optionality-fn**: one of two functions. either **required-arg**, or **optional-arg.** **required-arg** will throw an error if the binding is missing or malformed. **optional-arg** allows missing bindings to pass

**transform-fn** will transform the byte-string to some primitive type (number, boolean, etc.) or throw an error trying
and 

**contract-fn**, which is the actual domain-enforcing racket-contract we want to assert before we send the argument to the server

**(make-idl...)** returns a single function which operates on the **HTTP request-bindings**, and either returns a value which honors the description we memorialized in the four arguments, or throws an error

Usage and the missing helper functions will be discussed in Part II.

```racket
(require (prefix-in HTTP: web-server/http/request-structs)) 

(define/contract (make-idl            contract-fn
                                      transform-fn
                                      optionality-fn 
                                      binding-name)
  (-> contract? (-> any/c any/c) (-> any/c any/c) bytes? (-> (listof HTTP:binding?) any/c))
  (compose (λ (x) (if (not (contract-fn x))
                      (raise (exn:fail (format "IDL layer error: binding contract error\n" ) (current-continuation-marks)))
                      x))
           (λ (x) (if (not (transform-fn x))
                      (raise (exn:fail (format "IDL layer error: binding transformation error\n" ) (current-continuation-marks)))
                      (transform-fn x)))
           optionality-fn
           (λ (bindings) (HTTP:bindings-assq binding-name bindings))))

```


#### Cookies and the Web Server 

Two quick notes:

1) You can pass base64 encoded values to the browser as cookie-values as long as you strip both out the embedded and trailing carriage-return-line-feed sequences. 

**BAD:**
```racket
(define (start request)
  (response/xexpr `(html (head (meta ((name "viewport")(content "initial-scale=1.0, user-scalable=no")))
                               (meta ((http-equiv "content-type")(content "text/html; charset=UTF-8"))))
                                       (body (div "Cookies!")))
                  #:headers  (list (make-header #"Set-Cookie" #"Racketboy=XetM5o+My2BQYizra/y+NC7UJ0MxMjM0\r\nNTY2OQ==\r\n; Secure;"))))
```

**GOOD:**
```racket
...code...
#:headers  (list (make-header #"Set-Cookie" #"Racketboy=XetM5o+My2BQYizra/y+NC7UJ0MxMjM0NTY2OQ==; Secure;"))
...code...
```

2) The Secure flag in the cookie only instructs the **browser** not to send the cookie over a non-secure connection. The server will happily pass a Secure-flag cookie over a non-secure connection.

To prevent the a Secure-flag cookie from being sent over a non secure connection, set the #:ssl keyword argument to #t in serve/servlet.

#### AJAX and the Web Server 

I wanted to present an absolute minimal implementation of Jay's Web Server that demonstrates how to set up AJAX functionality.  

It doesn't do very much, but you can use as an AJAX test bed. I used this particular code to test whether setting browser cookies via AJAX works. 

```racket
#lang web-server
  
(require  web-server/servlet-env
          xml
          web-server/http/xexpr)

(define my-xml-response
  (response/xexpr `(xml "victory!")
                  #:mime-type #"text/xml charset=utf-8"
                  #:headers (list (make-header #"Set-Cookie" #"name=mikey"))))
  
(define (start request)
  (letrec ((response-generator (λ (make-url)
                                 (response/xexpr `(html (head 
                                                         (script ((type "text/javascript")) ,(format StartXMLHttpRequest (make-url receive-ajax-signal)))
                                                         (script ((type "text/javascript")) ,processChange)
                                                         )
                                                        (body (div ((onclick "alert('things are working');"))  "Hello jay")
                                                                     (div ((onclick "StartXMLHttpRequest('some data');"))  "click for AJAX-type Request")
                                                                     (a ((href ,(make-url receive-signal)))"click for browser-window-type Request"))))))
           (receive-ajax-signal   (λ (request)
                                    my-xml-response))
           (receive-signal (λ (request)
                              (send/suspend/dispatch response-generator))))
    (send/suspend/dispatch response-generator)))


(define StartXMLHttpRequest (string-append "function StartXMLHttpRequest(post_data){ "
                                           "obj = new XMLHttpRequest(); "
                                           "obj.onreadystatechange = processChange;"
                                           "obj.open('POST','~A',false); "
                                           "obj.setRequestHeader('Content-Type','application/x-www-form-urlencoded'); "
                                           "obj.send(post_data); "
                                           "processChange();"
                                            "} "))

                 
(define processChange "function processChange(){alert('in processChange!');}")
                                           

(serve/servlet start
               #:stateless? #t        
               #:launch-browser? #t
               #:connection-close? #t
               #:quit? #f 
               #:listen-ip #f 
               #:port 8000
               #:servlet-path "/")
```


#### Generating a GUID using the Win32 API

Demonstrates use of the Foreign Function Interface (FFI) to create a Globally Unique ID

```racket
#lang racket

#|
creates a GUID using the Win32API via the foreign function interface

usage:
(new-GUID) ; ->"3849203981-8836-19662-12178292003955076235"

;returns a max(43) length string, which we can store in database
and set a UNIQUE constraint to make sure same order isn't entered twice.
|#

(require  ffi/unsafe)

(provide new-GUID)

(define ole32 (ffi-lib "ole32.dll"))

(ffi-lib? ole32)

(define-cstruct _GUID ([Data1 _uint32]    ;32 bytes, max 10 char when converted to string
                       [Data2 _uint16]    ;16 bytes, max 5 char when converted to string
                       [Data3 _uint16]    ;16 bytes, max 5 chars when converted to string 
                       [Data4 _uint64]))   ;simulates 8x8 char array for 64 bytes total, max 20 chars when converted to string       

(define generate-GUID  (get-ffi-obj "CoCreateGuid" ole32 (_fun  _GUID-pointer -> _uint32)))
  
(define (new-GUID)
  (let* ((x (make-GUID 0 0 0 0)) ;note make-GUID returns a pointer to a _GUID structure
        (res (generate-GUID x)))
    (if (= res 0)
        (string-append 
         (number->string (GUID-Data1 x)) "-"
         (number->string (GUID-Data2 x)) "-"
         (number->string (GUID-Data3 x)) "-"
         (number->string (GUID-Data4 x)))
        (error "Unable to generate GUID"))))
  

```

#### Sending a file to the Windows Print Spool using the Win32 API


Uses the on-error-resume-next macro from above in the postlude. Also uses an anaphoric lambda (aλ) macro which I haven't posted yet. Can just substitute a letrec form if the a-lambda is confusing.


```racket
#lang racket\base

(require ffi/unsafe
         racket/function
         racket/path)

(define kernel (ffi-lib "kernel32.dll"))
(define winspool (ffi-lib "winspool.drv"))

(define-cstruct _DOC_INFO_1  ([pDocName _string/utf-16 ]
                              [pOutputFile _string/utf-16] 
                              [pDatatype _string/utf-16]))

;just return h, if its zero, then assume an error has occured
(define open-printer (get-ffi-obj "OpenPrinterW" winspool (_fun   _string/utf-16 (h : (_ptr o _uint32)) _pointer -> (r : _uint32) -> h)));(values h r))))
(define get-last-error (get-ffi-obj "GetLastError" kernel (_fun -> _uint32)))
(define start-doc-printer (get-ffi-obj "StartDocPrinterW" winspool (_fun _uint32 _uint32 _DOC_INFO_1-pointer -> _uint32)))
(define start-page-printer (get-ffi-obj "StartPagePrinter" winspool (_fun _uint32 -> _uint32)))
(define write-printer (get-ffi-obj "WritePrinter" winspool (_fun _uint32 _pointer  _uint32 (read : (_ptr o _uint32)) -> (r : _uint32) -> (values read r))))
(define end-page-printer (get-ffi-obj "EndPagePrinter" winspool (_fun _uint32 -> _uint32)))
(define end-doc-printer (get-ffi-obj "EndDocPrinter" winspool (_fun _uint32 -> _uint32)))
(define close-printer (get-ffi-obj "ClosePrinter" winspool (_fun _uint32 -> _uint32)))


;usage (spool-file (build-path  "C:\\temp.doc") "printername")
(define (spool-file pth szprinter)
  (let ((hprn 0))
    (dynamic-wind
     (λ _ void)
     (λ _ (define buf-size #x4000)
       (set! hprn (ON-FAIL  (open-printer szprinter #f) (format "spool-file; unable to open printer ~A" szprinter)))
       (let ((di (make-DOC_INFO_1  (string-append "Box-lunch:" (path->string (file-name-from-path pth))) #f "RAW")))
         (ON-FAIL  (start-doc-printer hprn 1 di) "spool-file: failed to start document")
         (ON-FAIL  (start-page-printer hprn) "spool-file: failed to start page")
         (let ([buffer (make-bytes buf-size (char->integer #\_))])
           (with-input-from-file pth
             (λ _ 
               ((aλ (bytes-read)
                    (unless (eof-object? bytes-read)
                      (let-values ([(written retval) (write-printer hprn buffer  bytes-read)])
                        (ON-FAIL retval "spool-file: failed to write to printer"))
                      (self (read-bytes! buffer))))
                (read-bytes! buffer)))
             #:mode 'binary))
         ))
     (λ _ (on-error-resume-next (end-page-printer hprn)
                                (end-doc-printer hprn)
                                (close-printer hprn))))))



;raises an error if id isn't a positive integer. Zero is typically returned for a win32 error
(define/contract (ON-FAIL id msg)
    (-> any/c string? exact-positive-integer?)
    (unless (exact-positive-integer? id)
        (raise (exn:fail msg (current-continuation-marks))))
    id)

```  

##### Quickly create a large file (e.g. for testing, or to reserve disk space for later use)

```
(file-position (open-output-file (make-temporary-file)) (* 1024 1024)) ;; 1MB zero-filled file
```

##### More convenient printing of multiple values

```
(define-syntax (say stx)
  (syntax-case stx ()
    [(_ a b ...)
     #'(displayln (~a a b ...))]))
```

Use as follows:

```  
(say "The value of x is: " x)
```
