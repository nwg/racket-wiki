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

