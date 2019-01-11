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
[[How to transform a Tree (see above) into an x-expression]]  
[[Web Server: Creating an Interface Definition Language (IDL) between an HTTP-request and Racket code, Part I|Creating an Interface Definition Language]]  
[[Cookies and the Web Server]]  
[[AJAX and the Web Server]]  
[[Generating a GUID using the Win32 API]]  





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
